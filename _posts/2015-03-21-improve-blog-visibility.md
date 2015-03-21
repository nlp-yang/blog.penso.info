--- 
layout: post
title: Improving your Blog visibility
categories: 
- computer
description: I spent years running this blog, this is a list of tricks to improve your blog visibility
---

TL;DR — **I spent years running this blog, and if you look at my page rank or
search for any subject I blogged about, you'll find out I've achieved a pretty
good score. This is a list of tricks I did to achieve this.**

Recently I moved my Blog from WordPress to Jekyll, and got the feeling to blog
again. I've always blogged for years, but Facebook, Twitter and other social
networks kind of took over for short thoughts[^0]. And I only had short
thoughts the past years.

Improving your blog visibility can be summarized in 6 steps:

1. Make your website load as fast as possible
2. Generate clean HTML, include meta description tags and clear title
3. Integrate social networks metas for Twitter and Facebook
4. Sitemaps, to help search Engines
5. Microformats
6. RSS Feeds and ping the oustide World once you wrote new content

* * * * *

## Load as fast as possible

> The speed at which your blog loads is critical to attracting more readers to
> your blog. If your blog takes a long time to load, many readers may leave your
> blog before they have the chance to read it. 
>
> <cite>—[Google](https://support.google.com/blogger/answer/42394?hl=en)
{: .pullquote }

#### A. Find your current website slow points

Don't underestimate your loading speed. You should make your website load as
fast as possible. [Google](http://www.google.com) indexes you better, and
visitors won't mind about reading and clicking around your blog if each page
loads under seconds.

This is so important Google spends a huge amount of money improving website
delivery. Android caches images through their proxy when you browse and rewrite
images from JPEG to WEBP on the fly to save 30%. Every millisecond they save
showing pages while you browse results in more money for them. You browse more,
they show more ads, they make more money. As simple as that.

[PageSpeed
Insights](https://developers.google.com/speed/pagespeed/insights)[^1] by Google
will list all current issues and how to fix your slow points, while
[Pingdom](http://tools.pingdom.com/fpt/ePnTcP/http://blog.penso.info)[^2] will
tell you how fast your website loads compared to others.

As an example, I use [nginx](http://wiki.nginx.org/Main) as my main webserver
and PageSpeed requested for a few changes like gzip compression. I was aware of
such possibility but forgot I had not enabled it on my blog. You can read my 
[full nginx configuration file](https://gist.github.com/penso/5888446).

#### B. Use a CDN

Using a CDN for your JS/CSS will improve your speed. You used to have to pay a
lot for this, but it's now very easy as
[CloudFlare](https://www.cloudflare.com/) is hosting most Javascript frameworks
at [cdnjs](http://cdnjs.com/) free of charge.

Using a CDN allows visitors to fetch data from closer servers, frees your
server from serving them and you'll only benefit from this. I also suggest only
using [minified version](http://cssminifier.com/) of the CSS and [the
Javascript files](http://jscompress.com/).

Your HTML should look like:

{% highlight html %}
<link href="//netdna.bootstrapcdn.com/twitter-bootstrap/2.3.2/css/bootstrap-combined.min.css" rel="stylesheet" />
<link href="//netdna.bootstrapcdn.com/font-awesome/3.1.1/css/font-awesome.min.css" rel="stylesheet" />
<script src="//netdna.bootstrapcdn.com/twitter-bootstrap/2.3.2/js/bootstrap.min.js"></script>
{% endhighlight %}

#### C. Remove all unecessary CSS/Code

I personally removed the Facebook and Twitter Javascript SDKs to display share
or follow buttons. They're nice to have but they also slow your website a lot.
I don't think they're worth it.

#### D. Switch to a static blog system

![Speed improvement](/img/blog_speed.png)
{: .post_photo }

This graph from [Google Webmaster
Tools](https://www.google.com/webmasters/tools/home?hl=en) shows speed delivery
when I switched this blog to Jekyll. Whatever you choose, delivering static
pages through any website generator will give an order of magnitude
improvement. I suggest looking at [Jekyll](http://jekyllrb.com) or
[Middleman](http://middlemanapp.com/), they're both really good.

#### E. Move your static website to S3/Cloudfront

There is many online tutorials to do that, and I moved my blog to it as well. I
suggest you move your website to S3/Cloudfront as it'll improve deliverability
to your users, and it's so cheap it would be stupid not to use it.

This [s3_website gem](https://github.com/laurilehmijoki/s3_website) will allow
to do just that, easily.

* * *

## Clean your HTML and include basic tags

### Responsive design

If your blog doesn't work on mobile devices, you can stop blogging right now.
Frameworks like [Bootstrap](http://getbootstrap.com) makes this easy.

It used to be designing a website first then making sure it works on mobile,
but I would suggest starting with the mobile version and then move on to larger
displays.

### Blog titles: important

This is mostly where the magic happens, titles (and domain names) is the most
important part of your post. Use what you want users to search in Google to
find your post. I suggest adding your site title to the post title using the
pattern "post title — site title", like:

`
  Improving your blog visibility — Fabien Penso
`

[Google wrote a
post](http://googlewebmastercentral.blogspot.com.au/2012/01/better-page-titles-in-search-results.html)
about improving page titles for search results. Google will actually generate
alternate page titles if they feel yours aren't relevant enough.

Page titles have to [be
descriptive](http://support.google.com/webmasters/bin/answer.py?hl=en&answer=35624#3),
and concise. [This video](http://www.youtube.com/watch?v=L3HX_8BAhB4) from Matt
Cutts (Google) explains how Google choose titles for search results.


### Clean HTML

Clean HTML does matter for Google, the cleaner the HTML the best. I'm not sure
anyone has proofs of this but it can't hurt and I'm pretty sure it helps. You
can use the [W3C Markup Validation Service](http://validator.w3.org/) and see
[my website](http://validator.w3.org/check?uri=http%3A%2F%2Fblog.penso.info) as
an example.

You should use [Structured Data
Markup](https://developers.google.com/structured-data) as well (also named
microformats). They will allow you to give detailed information to Google about
how to show your content.

### Meta tags

Regular meta tags are as important as well, `description` and `keywords` are
the most important. It would looks like:

{% highlight html %}
<meta property="description" content="You’re living outside the US and want to get a job in San Francisco? This might help you getting one." />
<meta name="keywords" content="computer"/>
{% endhighlight %}

## Social Network Integration

### Twitter Cards

[Twitter Cards](https://dev.twitter.com/docs/cards) allows Twitter to fetch your
blog post details, and display them when anyone tweets. It allows users to view
your Twitter account screenname, even if someone doesn 't tweet you directly.

For example [Enkimn](http://twitter.com/Enkimn) tweets a link to my blog,
without mentionning me in his message. However the Tweet shows a photo, a
title, a description, my Twitter username and my name. I specified all of them
within meta tags in my HTML.

<blockquote class="twitter-tweet" lang="en"><p>Сонирхолтой.&#10;Энэ бүр &quot;I love Paris as much as I hate Parisians&quot; :)&#10;---&#10;Getting a job in San Francisco — Fabien Penso <a href="http://t.co/3GFR0Ulvb8">http://t.co/3GFR0Ulvb8</a></p>&mdash; Enkimn (@Enkimn) <a href="https://twitter.com/Enkimn/status/448842654315315202">March 26, 2014</a></blockquote> <script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

*Sometimes this photo disappears with old tweets, [this is what it looks
like](/img/twitter_card.png) if you're not seeing it in the embedded tweet.*

Read [the details about Twitter Cards](https://dev.twitter.com/docs/cards),
you'll want to implement the [Summary
Card](https://dev.twitter.com/cards/overview) and Use their
[Card Validator](https://cards-dev.twitter.com/validator) to
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

*While you can use [Twitter Cards](https://dev.twitter.com/docs/cards) without a
Twitter Account, I highly suggest creating one. It allows you visitors to talk
to you directly, and is a must-have for any blogger these days.*

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

## Sitemaps

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

## More tricks

### Newsletter

Don't underestimate email lists. This is the only way to make sure you connect
to your followers. Facebook pages, Twitter and pretty much every social
networks might change the way they allow you to contact with your followers.
Email won't change, and is more accessible to non-geeks than RSS feeds.

Ali Mese [wrote](https://medium.com/everything-about-startups-and-entrepreneurship/how-i-got-6-2-million-pageviews-and-144-920-followers-d4d3fa440802)
about how he got 6.2 million pageviews and 144,920 followers, and one advice is
to put an email form.

> After all those email campaigns, I have to confess that email is now by far the
> most effective marketing tool that works for me and for almost every one of my
> clients with no exception.
>
> <cite>—[Ali Mese](http://thenextweb.com/insider/2015/03/21/how-i-got-6-2-million-pageviews-and-144920-followers/)
{: .pullquote }


You can even automate emails with
[MailChimp](http://mailchimp.com/features/rss-to-email/) and their rss-to-email
feature.


### RSS Feeds

Even as of today, RSS feeds is still popular. If not by users, at least by
services publishing content and search engines. I suggest you add images into
the RSS feeds as well, and full length article.

### Pingomatic 

You just wrote a new master piece on your blog, and you want to tell everyone
**now** and not later. A very useful service will ping most services at once:
[Pingomatic](http://pingomatic.com/).

### Google Analytics

[Google Webmaster Tools](https://www.google.com/webmasters/tools/home?hl=en)
will allow you to check your blog analytics, it's free and highly recommended.

* * *

I hope you found this post useful. If you did, drop me a note at
[@fabienpenso](http://twitter.com/fabienpenso). If you didn't, drop me a note
anyway telling me how to improve it.

You can stay up to date via [my RSS feed](/atom.xml). Thanks for reading.


[^0]: I do read blogs a lot through my [Faast](http://app.faast.io) iOS app, actually I follow about 600 feeds realtime.
[^1]: I score 93 (out of 100) but those change overtime since Google always improve it.
[^2]: Says my website is faster than 99% of all tested websites, rerun a few time if you get a lower score.
