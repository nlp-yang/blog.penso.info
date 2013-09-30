--- 
layout: post
title: Improving your Blog visibility
categories: 
- computer
description: to be filled
---

You want to improve your website visibility to the outside World? This post
aims at helping you about that.

Recently I moved my Blog from WordPress to Jekyll, and got the feeling to blog
again. I've always blogged for years, but Facebook, Twitter and other social
networks kind of took over for short thoughts[^0].

I only had short thoughts the past years.

Today your blog will mostly get linked from Social Networks (Facebook, Google
Plus, Twitter), or be found through [Google](http://www.google.com) search. You
want to make sure you play nice with all of those.

Improving your blog visibility can be summarized in 6 points:

1. Make your website load as fast as possible
2. Generate clean HTML, include meta description tags and clear title
3. Integrate social networks metas for Twitter and Facebook
4. Sitemaps, to help search Engines
5. Microformats
6. RSS Feeds and ping the oustide World when you wrote new content

### Improve your blog loading speed

> The speed at which your blog loads is critical to attracting more readers to
> your blog. If your blog takes a long time to load, many readers may leave your
> blog before they have the chance to read it. 
>
> <cite>—[Google](https://support.google.com/blogger/answer/42394?hl=en)
{: .pullquote }

#### A. Find your current website slow points

Don't underestimate your loading speed. You should make your website load as
fast as possible. [Google](http://www.google.com) will index you better, and
visitors won't mind about reading and clicking around your blog if each page
loads under seconds.

Existing tools will help you finding about your current speed:

* [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights)[^1] by Google
* [Pingdom](http://tools.pingdom.com/fpt/ePnTcP/http://blog.penso.info)[^2]

[PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights)
will help you improving your website speed as it will list all current issues,
and how to fix them. I use [nginx](http://wiki.nginx.org/Main) as my main
webserver, some tags I added in my server:

	# This goes into a server block in NGINX
	location ~* \.(js|css|png|jpg|jpeg|gif|ico)$ {
		expires 1w;
		log_not_found off;
	}

	charset UTF-8;

	gzip             on;
	gzip_vary on;
	gzip_min_length  500;
	gzip_proxied     expired no-cache no-store private auth;
	gzip_types text/plain text/css application/x-javascript text/xml application/xml application/xml+rss text/javascript;

You can read the [full configuration file](https://gist.github.com/penso/5888446).

![Speed improvement](/img/blog_speed.png)
{: .post_photo }

This graph comes from [Google Webmaster
Tools](https://www.google.com/webmasters/tools/home?hl=en) and you can see the
speed improvements I had switching from [WordPress](http://www.wordpress.com)
to [Jekyll](http://jekyllrb.com).

#### B. Use a CDN

Using a CDN for your JS/CSS will improve your speed, thanksfully that's very
easy as [CloudFlare](https://www.cloudflare.com/) is hosting most Javascript
frameworks at [cdnjs](http://cdnjs.com/), for free. I use
[BootstrapCDN](http://www.bootstrapcdn.com/) for my
[Bootstrap](http://twitter.github.io/bootstrap/) CSS, and I include.

Using a CDN allows visitors to fetch those files from closer servers, and it
frees your server from serving them. You'll only benefit from this.

Only use minified CSS and Javascript files, that helps.

My HTML looks like:

	<link href="//netdna.bootstrapcdn.com/twitter-bootstrap/2.3.2/css/bootstrap-combined.min.css" rel="stylesheet" />
	<link href="//netdna.bootstrapcdn.com/font-awesome/3.1.1/css/font-awesome.min.css" rel="stylesheet" />
	<script src="//netdna.bootstrapcdn.com/twitter-bootstrap/2.3.2/js/bootstrap.min.js"></script>
	<script src="http://code.jquery.com/jquery.min.js"></script>

#### C. Remove all unecessary CSS/Code

I personally removed the Facebook and Twitter Javascript SDKs to display share
or follow buttons. They're nice to have but they also slow your website a lot.

* * *

## Clean your HTML and include basic tags

## Include social network tags

## Help search Engine indexing you: Sitemaps

## Help search Engine to figure out your data: Microformats


### Google Authorship

[Google Authorship](https://plus.google.com/authorship) allows you to specify who wrote your blog posts, chance are
it would be you only for all of yours. It allows Google to display your avatar
picture when your blog shows within the results. See the following image sample:

![Google Search example](http://f.cl.ly/items/1S402Y3x1e1r2n1p3W3R/Screen%20Shot%202013-06-02%20at%2023.25.56.png)

You should [signup for Authorship](https://plus.google.com/authorship):

1. Make sure you have a profile photo with a recognizable headshot on your
[Google Plus](http://plus.google.com) page.
2. Make sure a byline containing your name appears on each page of your content
(for example, "By Fabien Penso").
3. Make sure your byline name matches the name on your Google+ profile.
4. Verify you have an email address (such as foo@penso.info) on the same
domain as your content.

### Clean HTML

Clean HTML does matter for Google, the cleaner the HTML the best. I'm not sure
anyone has proofs of this but it can't hurt and I'm pretty sure it helps. You
can use the [W3C Markup Validation Service](http://validator.w3.org/) and see
[my website](http://validator.w3.org/check?uri=http%3A%2F%2Fblog.penso.info) as
an example.

### Twitter Cards

[Twitter Cards](https://dev.twitter.com/docs/cards) allows Twitter to fetch your
blog post details, and display them when anyone tweets. It allows users to view
your Twitter account screenname, even if someone doesn 't tweet you directly.

For example [Gergely](http://twitter.com/felhobacsi) tweets a link to my blog,
without mentionning me in his message. However the Tweet shows a photo, a
title, a description, my Twitter username and my name. I specified all of them
within meta tags in my HTML.

<blockquote class="twitter-tweet"><p>Getting a job in San Francisco <a href="http://t.co/Me5GoDnuun" title="http://blog.penso.info/2013/05/25/getting-a-job-in-san-francisco/">blog.penso.info/2013/05/25/get…</a></p>&mdash; Gergely Hodicska (@felhobacsi) <a href="https://twitter.com/felhobacsi/status/338982210361237506">May 27, 2013</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

Read [the details about Twitter Cards](https://dev.twitter.com/docs/cards),
you'll want to implement the [Summary
Card](https://dev.twitter.com/docs/cards/types/summary-card) and Use their
[Card Validator](https://dev.twitter.com/docs/cards/validation/validator) to
check your HTML metas. You'll have to validate and apply your HTML domain,
approval seems to be very fast (mine was done within hours).

As an example, [this
post](http://blog.penso.info/2013/05/25/getting-a-job-in-san-francisco/)
includes:

{% highlight html %}
<meta property="twitter:title" content="Getting a job in San Francisco" />
<meta property="twitter:description" content="You’re living outside the US and want to get a job in San Francisco? This might help you getting one." />
<meta property="twitter:card" content="summary" />
<meta property="twitter:site" content="@fabienpenso" />
<meta property="twitter:creator" content="@fabienpenso" />		
<meta property="twitter:image:src" content="http://farm6.staticflickr.com/5135/5419272408_5f5e08784a_z.jpg" />
{% endhighlight %}

### Twitter Account

While you can use [Twitter Cards](https://dev.twitter.com/docs/cards) without a
Twitter Account, I highly suggest creating one. It allows you visitors to talk
to you directly, and is a must-have for any blogger these days.

### Facebook OpenGraphs

[Facebook Opengraph](https://developers.facebook.com/docs/opengraph/) was
released before the [Twitter Cards](https://dev.twitter.com/docs/cards), and
allows [Facebook](http://www.facebook.com) to fetch your post details when a
user post a link to your blog.

It also use HTML meta tags. As a sample, [this
post](http://blog.penso.info/2013/05/25/getting-a-job-in-san-francisco/)
includes:

{% highlight html %}
<meta property="og:site_name" content="Fabien Penso" />
<meta property="og:type" content="article" />
<meta property="og:image" content="http://farm6.staticflickr.com/5135/5419272408_5f5e08784a_z.jpg" />
<meta property="og:title" content="Getting a job in San Francisco" />
<meta property="og:description" content="You’re living outside the US and want to get a job in San Francisco? This might help you getting one." />
{% endhighlight %}

You can view a complete [OpenGraph documentation](http://ogp.me/), and use
[this console](https://developers.facebook.com/tools/debug) to verify your tags
are fetched properly.


### Newsletter

### Blog titles: important

This is mostly where the magic happens, titles (and domain names) is the most
important part of your post. Use what you want users to search in Google to
find your post. I suggest adding your site title to the post title using the
pattern "post title — site title", like:

`
  Improving your blog visibility — Fabien Penso
`

Last year [Google wrote a
post](http://googlewebmastercentral.blogspot.com.au/2012/01/better-page-titles-in-search-results.html)
about improving page titles for search results. Google will actually generate
alternate page titles if they feel yours aren't relevant enough.

Page titles have to [be descriptive](http://support.google.com/webmasters/bin/answer.py?hl=en&answer=35624#3), 

### RSS Feeds

Even as of today, RSS feeds is still popular. If not by users, at least by
services publishing content.

Tags in the headers + link

### Pingomatic 

You just wrote a new master piece on your blog, and you want to tell everyone
**now** and not later. A very useful service will ping most services at once:
[Pingomatic](http://pingomatic.com/).

### Sitemaps

[Sitemaps](http://en.wikipedia.org/wiki/Sitemaps) tells search engines what
links are available on your blog, how often to recrawl them, when they were
last updated, how important they are. View [the complete
format](http://www.sitemaps.org/protocol.html).

> Using this protocol does not guarantee that web pages will be included in
> search indexes, nor does it influence the way that pages are ranked in search
> results.

The following sample shows all available tags for your sitemap, and you can
also view [my complete sitemap](http://blog.penso.info/sitemap.xml).

{% highlight xml %}
<?xml version="1.0" encoding="utf-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
 <url>
  <loc>http://example.com/</loc>
  <lastmod>2006-11-18</lastmod>
  <changefreq>daily</changefreq>
  <priority>0.8</priority>
 </url>
</urlset>
{% endhighlight %}

### Page speed

Use http://cdnjs.com/
Use https://www.cloudflare.com

https://developers.google.com/speed/pagespeed/insights

My score: `The page Fabien Penso got an overall PageSpeed Score of 93 (out of 100)`

Pingdom: http://tools.pingdom.com/fpt/ePnTcP/http://blog.penso.info `Your website is faster than 99% of all tested websites`

### Micro formats

Testing : http://www.google.com/webmasters/tools/richsnippets?

URL : http://www.ihid.co.uk/blog/markup-your-blog-using-schema-org
URL : 

### Google Analytics

[Google Webmaster Tools](https://www.google.com/webmasters/tools/home?hl=en).

* * *

I hope you found this post useful. If you did, drop me a note at
[@fabienpenso](http://twitter.com/fabienpenso). If you didn't, drop me a note
anyway telling me how to improve it.

You can stay up to date via [my RSS feed](/atom.xml). Thanks for reading.


[^0]: I do read blogs a lot through my [Push4](http://2apn.com) iOS app, actually I follow about 600 feeds realtime.
[^1]: I score 93 (out of 100)
[^2]: Says my website is faster than 99% of all tested websites
