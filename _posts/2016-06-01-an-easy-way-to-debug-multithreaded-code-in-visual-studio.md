---
title: An easy way to debug multithreaded code in Visual Studio
layout: post
date: 2016-06-01 4:18:42 +0000
tags: [visual studio, debugging]
---
If you ever have debugged multithreaded code, then you know what pain it can be. You jump around all over the place, value constantly changes. It's hell. But there is a way in Visual Studio to only debug a single thread.

Start by setting a breakpoint anywhere you need to debug, like you normally would. Once you hit the breakpoint and you are in the thread you want, go to the Visual Studio Threads window. It can be found under "_Debug > Windows > Threads_" while debugging.

Select all threads except the one you want to debug, then right-click and choose "Freeze". Now, Visual Studio will only step through the thawed thread. It seems to be much slower when doing this, presumably because it has to loop through all of the frozen threads, but it brought some sanity to my multithreaded debugging.
