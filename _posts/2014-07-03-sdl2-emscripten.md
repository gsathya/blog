---
layout: post
title:  "Emscripten port of SDL2"
date:   2014-07-03 11:30:11
comments: true
categories: mozilla
---

I've been working on porting [SDL2](https://www.libsdl.org/) to
Javascript using [Emscripten](https://www.emscripten.org) as part
of my summer internship at [Mozilla](https://www.mozilla.org/). 
Most of my work has been based off a community started [port](https://github.com/Daft-Freak/SDL-mirror/).

I recently posted a HOWTO on using my SDL2 port on the emscripten
mailing list, and I figured I should put it up here for others to
find as well.

First, clone and cross compile SDL2 -

{% highlight bash %}
* $ git clone https://github.com/gsathya/SDL-emscripten.git
* $ cd SDL-emscripten/
* $ emconfigure ./configure --host=asmjs-unknown-emscripten  \
    --disable-assembly --disable-threads --enable-cpuinfo=false  \
    CFLAGS="-O2"
* $ emmake make
{% endhighlight %}

Now the SDL2 port is built in ```/path/to/SDL-emscripten/build/.libs```

You can include the headers by adding ```-I/path/to/SDL-emscripten/include```
to the ```emcc``` command and then including SDL itself by just adding the
path to the built lib.

So if previously your command was something like -

{% highlight bash %}
$ emcc foo.c -o a.html
{% endhighlight %}

it changes to
{% highlight bash %}
$ emcc foo.c -I/path/to/SDL-emscripten/include \
    /path/to/SDL-emscripten/build/.libs/libSDL2.a -o a.html
{% endhighlight %}


The current status of the SDL2 test suite is on the [wiki](https://github.com/gsathya/SDL-emscripten/wiki/SDL-Tests). Feel free to fork it and send me pull requests!



