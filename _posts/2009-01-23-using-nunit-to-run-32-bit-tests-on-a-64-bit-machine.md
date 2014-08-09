---
layout: post
title:  Using NUnit to run 32-bit tests on a 64-bit platform
date:   2009-01-23 14:58
tags:   nunit
---
Esoteric? Yes. But, these are the problems I run into…

I recently installed the 64-bit version of Windows Vista in order to gain access to all 4GB of memory on my computer. (32-bit versions of Windows can only access about 3.5GB.) But, when I tried to run some NUnit tests, I started running into problems.

First, my tests use the Microsoft Jet driver to access a Microsoft Excel spreadsheet. Unfortunately, there is no 64-bit version of the Jet driver. So, when I tried to execute my tests, they failed to load the driver.

64-bit Vista does come with a 32-bit version of the Jet driver. In order to access the 32-bit driver, your code must be 32-bit. So, I told Visual Studio to use the x86 configuration rather than the “Any CPU” configuration.

But, once I recompiled, NUnit refused to load my 32-bit DLL. It claimed that it could not load the DLL or one of its references:

<img src="/img/posts/assembly-not-loaded-dialog.jpg">

Turns out that NUnit was also compiled with the “Any CPU” option. So, when it launches on my 64-bit computer, it runs as a 64-bit app. This means that it cannot load 32-bit DLLs. Thus, the error.

The solution was to use a utility called CORFLAGS to add a 32-bit flag to NUnit.exe. Here’s the command I used:

`corflags nunit.exe /32BIT+`

Here’s a link to [the article I found explaining this](http://geekswithblogs.net/Lance/archive/2006/12/28/102191.aspx).
