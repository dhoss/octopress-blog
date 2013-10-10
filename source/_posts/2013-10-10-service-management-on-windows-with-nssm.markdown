---
layout: post
title: "Service management on Windows with nssm"
date: 2013-10-10 10:42
comments: true
categories: [devops, windows]
---

I'm not a Windows user by any stretch of the imagination, so this was really nice to find: [nssm (non-sucking service manager)](http://nssm.cc/).

I needed to set up [Fitnesse](http://fitnesse.org) as a Windows service so all users running it could see Firefox being spawned and the [Selenium](http://seleniumhq.org) tests being run.  I attempted to use the [Java Service Wrapper](http://wrapper.tanukisoftware.com/doc/english/download.jsp), but was disappointed to find that you have to purchase a license for any long term use.  After some more Googling, I happened upon the nssm mentioned earlier.

Here's what I did:

 1. Install nssm.
 2. Open up a terminal (or whatever the hell Windows folks call it) and type in the following:
    `nssm.exe install FitnesseService`
 3. A prompt will pop up, asking for:
   1. the path to the executable (mine was something like `C:\Program Files\Java\jre7\bin\java.exe`)
   2. additional arguments to pass to the aforementioned executable (I passed: `-jar C:\path\to\fitnesse-standalone.jar -d C:\path\to\fitnesse\wiki\data -p 8080`)

That was it.  Now I'm able to do `net start FitnesseService`, navigate to `http://localhost:8080`, and the Fitnesse server loads properly.
