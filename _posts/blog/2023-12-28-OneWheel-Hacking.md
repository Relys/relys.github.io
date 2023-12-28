---
layout: post
title: "Reverse Engineering the OneWheel"
modified: 2023-12-28
categories: blog
excerpt: "My Journey in Reverse Engineering the OneWheel: Safety, Rights, and Innovation"
tags: [OneWhee]
image:
  feature:
date: 2023-12-28
comments: true
share: true
---
Embarking on a New Adventure
Over the past year, I dove headfirst into an ambitious project: reverse engineering the Future Motion Onewheel. My journey in the realm of technology isn't new; my past exploits in crafting 0day vulnerabilities and developing custom homebrew libraries for the Nintendo Wii U and 3DS had set the stage. Yet, this project was different - it was about a device I use and love, the OneWheel.

United for a Greater Good
Our mission was driven by two primary objectives: advocating for the right to repair and improving the safety of Onewheel users. We believed that unlocking the mysteries of the Onewheel's firmware would enable us to make meaningful contributions to the community.

The Initial Breakdown
The journey began with the disassembly of the Onewheel, focusing on its STM32F3 microcontroller. Our approach was methodical, drawing inspiration from a sophisticated multi-stage low-level attack detailed in a USENIX paper (https://www.usenix.org/system/files/woot20-paper-obermaier.pdf). This method was our roadmap to accessing the firmware.

The Breakthrough
We employed voltage glitching and FPB hijacking, a challenging yet exhilarating process. This technique was pivotal in spawning a privileged shell, allowing us full access to the system. Upon analyzing the dumped firmware with Ghidra, we uncovered a critical aspect: the Onewheel's use of asymmetric AES encryption without key signing. This discovery hinted at the potential to exploit the OTA update process for code execution on the device.

Crafting a Solution
Our response was to create custom open-source firmware. This wasn't about breaking the system for the sake of it; our ethos was rooted in responsible and ethical hacking. We strategically designed our firmware to extract the bootloader that contained the key, instead of distributing the key itself. This approach not only aligned with our ethical standards but also with the broader community's right to knowledge and repair.

Confronting Challenges
Our journey wasn't without hurdles. Future Motion issued a DMCA takedown notice under the clause for creating a tool to bypass encryption. It was a complex situation, as we weren't distributing any intellectual property (IP) but merely providing a means for users to understand and repair their devices.

Advocating for Safety and Repairability
Our primary focus remained on underscoring the safety concerns surrounding the Onewheel and championing the right to repair movement. By sharing our findings and tools openly, we aimed to empower users, fostering a deeper understanding of their devices and advocating for safer, more repair-friendly products.

Reflecting on the Journey
This project was more than a technical endeavor; it was a journey through the intricate web of ethics, law, and technology. It reinforced the importance of balancing curiosity with responsibility, underscoring the fine line that exists in the world of reverse engineering. As we move forward, we remain committed to using our skills for the betterment of technology and its users.
