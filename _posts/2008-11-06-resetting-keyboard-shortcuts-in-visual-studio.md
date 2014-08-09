---
layout: post
title:  Resetting Keyboard Shortcuts in Visual Studio
date:   2008-11-06 10:25
tags:   visual-studio
---
Visual Studio just went schizophrenic on me: F5 started running File/Open/File,
rather than Debug/Start Debugging; F9 refused to toggle breakpoints; and, none
of the other default keyboard shortcuts appeared to be working normally. It
took me a while to find the resolution to the problem. So, I'm blogging it for
posterity.

In a Visual Studio Command Prompt, enter the following commands:

`devenv /resetuserdata`

This command clears out your recent projects list, dumps your RSS feed, and
more. It will execute for several seconds (perhaps even a minute), then return
control to the command prompt. (Interestingly, the /resetuserdata switch does
not appear to be documented – either in the command line help, or on MSDN. I
found it on a blog, which I cannot seem to relocate.)

`devenv /resetsettings`

This command starts Visual Studio. Go ahead and close Visual Studio.

`devenv`

This command starts Visual Studio again, and allows you to choose your
development environment defaults.

These commands did the trick for me in Visual Studio 2008. I believe they would
also work with Visual Studio 2005, but I have not confirmed this.
