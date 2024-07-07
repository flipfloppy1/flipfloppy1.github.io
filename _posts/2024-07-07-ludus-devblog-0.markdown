---
layout: post
title:  "Ludus Devblog 0"
date:   2024-07-08 00:35:56 +0930
categories: ludus devblog
comments: true
---

Welcome to the first ever Ludus Devblog! Here I'll update you on what has been going on with this elusive project, including its current status and what I've done so far.

Essentially: not much at all, really.

## VidentiUI

This is what I'm working on currently, and is one of the things that I'm going to keep [open-source](https://github.com/flipfloppy1/VidentiUI) and (relatively) renderer agnostic. To this end, VidentiUI allows you to bring your own rendering backend with you, much like projects such as [RmlUI](https://github.com/mikke89/RmlUi) and the better known [Dear Imgui](https://github.com/ocornut/imgui) (everything's an 'ui'!).

What's unique about VidentiUI is that it uses a system where every UI element is its own independent object, instantiated in a script called at the start of the app (or whenever you like, really). This, plus its scripting capabilities powered by the almighty Lua, allows it to do some really cool stuff, really easily. 

### start.lua
{% highlight lua %}
ui = { };
ui.buttons = { }
ui.buttons.button1 = { position = { x = 0.0, y = 0.0 },
dimensions = { x = 1.0, y = 1.0 },
color = { r = 0, g = 0, b = 0, a = 255 },
texture = ""};
time = 0.0;
VUI_nextScript = "resources/update.lua";
{% endhighlight %}

### update.lua (runs every frame)
{% highlight lua %}
time = time + VUI_dt;
ui.buttons.button1.color.r = math.sin(time) * 127.5;
ui.buttons.button1.color.g = math.cos(time) * 127.5;
ui.buttons.button1.color.b = math.sin(time + 3.14159/2) * 127.5;
{% endhighlight %}

### The Result
<img src="/images/ludus-devblog-0/vui-result.gif" width="540" />

It looks a lot smoother than that when rendered, trust me! (or better yet, [build it yourself](https://github.com/flipfloppy1/VidentiUI) and see!)

While its not suited to the web, since it's not a document format, its flexibility works well for games and similar real-time apps. At least, this is the idea behind it all. The library is still in *very* early development, so things might shift around a lot. As an example of this, the first iteration of VidentiUI, including its predecessor in Ludus (not in VUI commit history) used JSON for specifying elements, but when I realised how rigid that made the framework I decided to pivot to Lua, which is working quite well so far.

## The Other Stuff

Apart from VidentiUI, there's not much going on with Ludus at the moment.

I want a proper UI system that is comfortable to use before I move on to world generation with square-diamond noise (the "Next Step"). Other things on the roadmap is a modular entity system, and simulating an NPC's brain (so, very cool stuff).

There are a few things I can show you though.

### Old UI and Current World-gen/Renderer
<video controls src="/videos/ludus-devblog-0/ludus-demo.mp4" title="Early Ludus Demo" width="540"> </video>

### Dark Mode!!!
<img src="/images/ludus-devblog-0/dark-mode.png" width="540" />

### The Fabled "Battery Acid Dimension" (Issues with interpreting color data)
<img src="/images/ludus-devblog-0/battery-acid-dimension.png" width="540" />

### Final Words

If you want to see how this project goes, check back on the blog every now and then. I may consider creating a discord server for the project as [Finding Fortune](https://www.youtube.com/@Finding_Fortune/) and [Ethan Gore](https://www.youtube.com/@ethangore8697) have found great success in. 

As for future blog posts, I'll probably have a comparative analysis of a couple of video games and their horror elements coming up--so stay tuned for that (it'll be at least mildly interesting I swear). Otherwise, you'll probably see some more status updates on VidentiUI, and some things about world-gen once I eventually get around to implementing that for real. 

Have a good one, and don't forget to check out the [VidentiUI repository](https://github.com/flipfloppy1/VidentiUI) if you're looking for a UI library for a C++ game, or you're even a little interested in what's about.