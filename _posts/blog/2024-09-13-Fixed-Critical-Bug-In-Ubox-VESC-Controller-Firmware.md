---
layout: post
title: "Fixed Critical Bug In Ubox VESC Controller Firmware"
modified: 2024-09-13
categories: blog
excerpt: "Triaging and resolving a critical bug causing ESC shutoff while riding."
tags: [OneWheel, VESC]
image:
  feature:
date: 2024-09-13
comments: true
share: true
---
# Backstory
About three weeks ago a user reported some weird behavior for a specific ESC in the main VESC Discord channel regarding it shutting down when using a momentary button and having an idle timeout set despite the board being on. We were able to reproduce the issue and sure enough the board shutoff at exactly 1 minute that I had him configure. I pinged a few people in chat and then went back to work and proceeded to forget about it.

Yesterday, one of my friends reported the same issue which ended up causing some pretty bad road rash so I decided that I guess I'm spending my Friday evening debugging code...
# Fixing the code
In 6.02 there was #ifdef HW_SHUTDOWN_HOLD_ON in shutdown.c. In hw_ubox_100_core.h we do not define HW_SHUTDOWN_HOLD_ON so none of that shutdown code is included.

In 6.05 this was changed to split up sections in shutdown.c for HW_SHUTDOWN_HOLD_ON and then an else statement for latching switches (to support COMM_SHUTDOWN I assume).

Therefore in 6.05, the ubox still doesn’t have HW_SHUTDOWN_HOLD_ON defined, but since there’s an else statement in shutdown.c it will now include that code which completely fucks up the ubox implementation.

I have resolved this by Including a #ifdef HW_SHUTDOWN_CUSTOM in shutdown.c and then refactoring a few functions in hw_ubox_100_core.c so they are compatible with how shutdown_init() and do_shutdown() are called now in the rest of the code to support COMM_SHUTDOWN.

I then proceeded to submit the code as a hotfix upstream: https://github.com/vedderb/bldc/pull/766

You can find pre-compiled binaries here: 
