--- 
layout: post
title: Realtime update with Highcharts, Rails and SSE
categories: 
- computer
description: Realtime update with Highcharts, with Rails and SSE.
date: 2015-08-08 13:15:00 +02:00
author: Fabien Penso
photo: http://penso.info/img/realtime-highcharts.jpg
---

TL;DR — I started writing this article a long time ago while I was working for
[@mickael](https://twitter.com/mickael) at
[ProcessOne](https://www.process-one.net/en/). I never finished this article
and a few things changed since but it might still help you to do realtime
analytics for your service.

While I now work for [Cloudscreener](http://www.cloudscreener.com) as their CTO
I highly recommend to join [@mickael](https://twitter.com/mickael) if you work
in Instant Messaging.

__Just looking for the code?__ Check [<i class="icon-github"></i> this github
repository](https://github.com/penso/blog-sse/).

***

When I need to show realtime analytics to users I use:

 * [Batsd](https://github.com/noahhl/batsd) for storing datapoints.[^1]
 * [Highcharts](http://www.highcharts.com) to display the datapoints.
 * Server Side Events for the realtime part in the browser.

I
[patched](https://github.com/penso/batsd/commit/1e4041ad198a29a99ea7f1209847ab21126a4d47)
batsd to send a PUBLISH Redis command everytime it stores a new entry. You can
easily subscribe to this to deliver realtime datapoints back to the browser.

[Batsd](https://github.com/noahhl/batsd) doesn't seem to be moving that much
the past year, and I would suggest looking for an alternative or just using the
original [statsd](https://github.com/etsy/statsd/).

[Highcharts](http://www.highcharts.com) is nice, but these days everyone
wants realtime and the charts alone isn't enough. We already use
[batsd](https://github.com/noahhl/batsd) (a
[statsd](https://github.com/etsy/statsd) replacement by
[37signals](http://www.37signals.com/), using Ruby) to store all analytics. It
includes a server you can poll to retrieve data, and I patched 
it to send a publish call through redis and its pubsub feature to get those
values realtime, it allows the SSE part of the application to get data
automatically through `em-hiredis`.

<iframe
style="width: 100%; height: 350px"
src="http://jsfiddle.net/fabienpenso/vPXms/4/embedded/result/">
</iframe>

### Part 1

This part doesn't cover everything, we'll just go through the setup of
[highcharts](http://www.highcharts.com), and pushing random data through SSE. You can see the code on the
github [blog-sse](https://github.com/penso/blog-sse) repository, and if you
look at [each commits](https://github.com/penso/blog-sse/commits/master) from
the [initial
one](https://github.com/penso/blog-sse/commit/e4d1e414297797d42874b810d38a722d120c658b)
you can pretty much see each diff adding features.

We use a complete async stack through `sinatra-sse` and you therefor need to
use `thin` for the development server, and `rainbows` for the production part.
So the Gemfile includes:

    gem 'sinatra'
    gem 'sinatra-sse'
    gem 'thin'

#### Commits

The following commits will help you setting things up:

- [commit](https://github.com/penso/blog-sse/commit/82f245c7f8dc353eb3336372230b88fb8cc84fc3)
	showing you how to set [highcharts](http://www.highcharts.com), displaying
	random values from within Javascript itself (no SSE).
- [commit](https://github.com/penso/blog-sse/commit/9a2b95e13286348f67be140d7981813d5ded2c9d)
	showing you how to connects to SSE, exposing a `sinatra` server through the
	`mount` routes method.

#### Highcharts configuration

What took me a while to figure out, [you need to
prefill](https://github.com/penso/blog-sse/blob/master/app/assets/javascripts/application.js#L50)
points to [highcharts](http://www.highcharts.com/), as it will only keep a fixed amount of points (you can
change that in the settings but it doesn't look so good) and then you [call the
SSE](https://github.com/penso/blog-sse/blob/master/app/assets/javascripts/application.js#L61)
with `new EventSource`, and use [this
callback](https://github.com/penso/blog-sse/blob/master/app/assets/javascripts/application.js#L68)
to add points to the existing [highcharts](http://www.highcharts.com/) graph.

#### SSE Rails configuration

I use `sinatra-sse` which takes care sending an empty line to the browser [every
28
seconds](https://github.com/radiospiel/sinatra-sse/blob/master/lib/sinatra/sse.rb#L26)
to keep connected, it's a small gem. You can then use it to [push new
data](https://github.com/penso/blog-sse/blob/master/lib/realtime_analytics.rb)
to the client.

#### Nginx

If you don't see values coming from SSE, you might be using a [nginx]() proxy.
Nginx buffers the data from thin, and won't send anything to the browser before
about 20 or 30 seconds, to fix this you must add `proxy_buffering off;` to your
server:

    server {
     root /home/penso/push_console/public/;
     index index.html index.htm;
     server_name localhost;

     location / {
      proxy_set_header  X-Real-IP  $remote_addr;
      proxy_set_header  X-Forwarded-For $proxy_add_x_forwarded_for;
      proxy_set_header Host $http_host;
      proxy_redirect off;
      proxy_max_temp_file_size 0;
      proxy_buffering off; # <----------- here

      if (-f $request_filename) {
       break;
      }

      if (-f $request_filename/index.html) {
       rewrite (.*) $1/index.html break;
      }
      if (-f $request_filename.html) {
       rewrite (.*) $1.html break;
      }

      if (!-f $request_filename) {
       proxy_pass http://localhost:3000; # <--- redirection to thin
       break;
      }
     }
    }

### Part 2

The idea is to use `em-hiredis` do fetch data from redis. Write a `sinatra` app
looking like:

    require 'em-hiredis'
    class AnalyticsSSE < Sinatra::Base
      get '/' do
        sse_stream do |out|
          ActiveRecord::Base.connection_pool.with_connection do
            bucket_name = params[:id]
            redis.pubsub.subscribe(bucket_name) do |msg|
              unless msg.blank?
                out.push event: bucker_name, data: msg.to_json
              end
            end
          end
        end
      end
    end
    
    # and add it to your routes like:
    MyApp::Application.routes.draw do
      mount AnalyticsSSE: '/realtime-analytics'
    end

Calling your URL as you can see [in my
code](https://github.com/penso/blog-sse/blob/master/app/assets/javascripts/application.js#L61)
allows you to receive real-time datapoints, you can finally add them to you
graphs.

***

You can reach me at [@fabienpenso](http://twitter.com/fabienpenso).

[^1]: Batsd doesn't get love anymore, I recommend going to statsd instead.
