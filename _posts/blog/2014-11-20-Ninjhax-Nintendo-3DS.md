---
layout: post
title: "Ninjhax"
modified: 2014-11-20
categories: blog
excerpt: "Ninjhax Hack: 3DS Homebrew Exploit (Known as SSSpwn) Tutorial."
tags: [3ds-homebrew-ninjhax]
image:
  feature:
date: 2014-11-20
comments: true
share: true
---
Running http://smealum.net/ninjhax/ on my 3DS's.

Press UUDDLRLRAB for secret menu

One 3DS on sysnand 4.4.0-10U, one on emunand 9.2.0-20U and one on sysnand 9.2.0-20U.

If you want to look into how this exploit works use my NCCH decryptor (https://github.com/Relys/3DS_Multi_Decryptor) to decrypt Cubic Ninja .3DS and ctrtool to extract the .code portion from the ExeFS.bin Then load up the extracted code.bin in IDA and find the functions that handle the QR loading. From there it's just understanding how the overflow works. Next you can piece together the payload and reverse the ROP chain. To determine how the rop gadgets work you will have to have the binaries from which they are called from. :)  This means you will have to have RAM dumps (kernel access) or the title keys to decrypt from the CDN (https://github.com/Relys/3DS_Multi_Decryptor) for the firmware version you're targeting.

So, I haven't fully looked into it yet. But I think it works along these lines:
1. QR Code Overflow
2. Jump to ROP chain in QR code payload
3. Download AES encrypted payload smealum.net/ninjhax/p/POST5_WEST_4096_4096.bin from internet.
4. Escalate privilege level by exploiting a sysmodule and installing a new service used to launch .3dsx.
5. Transfer execution over to boot.3dsx

<iframe width="560" height="315" src="//www.youtube.com/embed/Kev-C6m1P9o" frameborder="0"> </iframe>


