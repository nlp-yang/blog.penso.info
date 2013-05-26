---
layout: post
author: Fabien Penso
title: ! 'Git GUI Mac client : why you don''t use it (yet)'
date: 2011-06-18 22:07:47.000000000 +02:00
categories:
- computer
---
I've spent the last weeks asking around to my fellow developers friends why they use the git command line tool instead of a nice GUI. Years ago when I was using Linux some people were just against GUI tools, but today they're not anymore. The reason they don't use a GUI is there is no current application good enough for replacing the <em>git command line</em>.

The existing tools like <a href="http://gitx.frim.nl/">Gitx</a>, <a href="http://www.git-tower.com/">Tower</a>, Gitk, <a href="http://gitmacapp.com/sprout">Sprout</a>, <a href="https://github.com/Caged/gitnub/wiki/">Gitnub</a> are all very similar in the way they do things, they are only improved tool of a basic Gitk but nothing than actually makes you want to use it full time.

I know, you think this is a useless application, git in command line is good enough. But you'd probably say the same thing about <a href="http://www.github.org">Github</a> 4 years ago, as you had your own servers, but it still became the de facto standard for Git source hosting today. Most of all because they added features noone thought about git at the time (easier pull, social coding, etc).

Questions coming to mind about a GUI Git application:
<ol>
	<li>Why you don't use a GUI?</li>
	<li>Why such a tool doesn't exist yet?</li>
	<li>What would make you use this tool?</li>
	<li>How long would it take to make such a tool?</li>
	<li>Would it be sustainable?</li>
</ol>
My answers:
<ol>
	<li>You don't use those GUI because they suck, if you use git you probably know what you're doing. Adding features slower to use in GUI than command line is a bad idea. You then basically run a GUI only to view branches and do visual things, once a week.</li>
	<li>A better tool doesn't exist because it's tough to develop, a new one need to find a new workflow, using complete different workflow than the existing bad ones.</li>
	<li>You would use the new tool because it saves you time, and allow not so advanced git user to do tricky things without knowing git as well. It also needs features for small groups, like push notifications when someone push code, local <a href="http://rubyforge.org/projects/gitjour/">gitjour</a> similar feature (share your git locally and discover others through Bonjour) for quick <em>hackathon</em>. You'd want a nice branch visual like the <a href="https://github.com/blog/39-say-hello-to-the-network-graph-visualizer">ones from github</a>, and a commenting system similar to github. You'd want full Github support, a live activity feed similar to <a href="http://basecamphq.com/">BaseCamp</a> listing commits, new comments. You'd want a light chat to reply live to commits, only for developers. You'd want more than just a git GUI.</li>
	<li>I think a beta version of such a Cocoa tool would take 3 months full time to get a beta, 6 months to get something working on a daily basis, for a team of at least 2 very good developers. There is a lot of thoughts to put in the design first.</li>
	<li>I can't say, but seeing <a href="http://www.github.org/">github</a> is bigger than <a href="http://code.google.com/">Google Code</a> and <a href="http://www.sourceforge.net">Sourceforge</a>, and everyone in <a href="http://maps.google.com/maps?q=san+francisco">San Francisco</a> has a mac laptop as a development laptop, I have the feeling such a tool, if popular, would be sustainable for a team of 3 people full time. San Francisco is a lot about trends, if you can make such a tool popular among a few top developers, there is a big change the others would follow.</li>
</ol>
