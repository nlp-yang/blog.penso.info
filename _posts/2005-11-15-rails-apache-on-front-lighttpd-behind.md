---
layout: post
author: Fabien Penso
title: Rails, Apache on front, lighttpd behind
date: 2005-11-15 23:48:00.000000000 +01:00
categories:
- rails
---
<p>I needed to use Apache on front because its mod_gzip plugin works pretty well and is efficient. Lighttpd doesn’t compress anything that ain’t static pages.</p>

<p>If you use that mode, rails will see requests coming from 127.0.0.1 and will keep displaying Routing error and not 404 pages even in production mode (rails does that for local request by default).</p>

<p>You’ll want to switch that off with the following piece of code. Paste it into the application_controller.rb file :</p>

<pre>
<code>
module ActionController
  module Rescue
    def local_request?
      false
    end
  end
end
</code>
</pre>

<p>And voilà, you have your usual 404 errors :)</p>
