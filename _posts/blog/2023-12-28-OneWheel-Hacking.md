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

# Navigating the Technical Terrain: Reverse Engineering the Future Motion OneWheel
Over the last year, I've embarked on a technically challenging and ethically nuanced project: reverse engineering the Future Motion OneWheel. This journey isn't my first foray into the complex world of technology - my background includes developing 0day vulnerabilities and custom homebrew libraries for gaming consoles like the Nintendo Wii U and 3DS. However, this endeavor with the OneWheel stands out due to its integration into my personal life and the potential impact on the user community.

# Mission: Right to Repair and User Safety
Our team's primary goals were twofold: advocating for the right to repair and enhancing the safety of Onewheel users. We hypothesized that by deciphering the OneWheel's firmware, we could contribute significantly to both these causes.

# Technical Deconstruction
The project commenced with a detailed teardown of the OneWheel, focusing primarily on its STM32F3 microcontroller. We adapted a complex, multi-stage low-level attack framework from a USENIX paper [Obermaier & Sigl, 2020](https://www.usenix.org/system/files/woot20-paper-obermaier.pdf) to navigate the system's defenses.

# Breakthrough via Voltage Glitching and FPB Hijacking
The process involved intricate voltage glitching and Flash Patch and Breakpoint (FPB) hijacking. This approach was crucial in creating a privileged shell, granting us comprehensive access to the system. Subsequent analysis of the firmware, using tools like Ghidra, revealed a significant detail: the use of asymmetric AES encryption in the Onewheel's firmware, notably lacking key signing. This raised the possibility of exploiting the Over-The-Air (OTA) update process for code execution.

# Ethical Development of Custom Firmware
In response, we developed custom open-source firmware. Our ethical standpoint was clear: we aimed to responsibly hack the system, prioritizing community empowerment over exploitation. Our firmware was designed to extract the bootloader containing the encryption key, avoiding the direct distribution of the key itself, thus adhering to our ethical standards and supporting the community's right to knowledge and repair.

# Legal Hurdles: DMCA Challenges
The project faced legal challenges when Future Motion issued a DMCA takedown notice, citing our tool's ability to bypass encryption. This situation was complex; our work didn't involve distributing intellectual property but provided a means for users to understand and repair their devices.

# Focusing on Safety and Repairability
Despite these challenges, our focus remained on highlighting safety issues with the OneWheel and advocating for the right to repair. By openly sharing our findings and tools, we aimed to empower users, fostering a deeper understanding of their devices and advocating for safer, more repair-friendly products.

# Reflections: Ethics, Law, and Technology
This project transcended mere technical exploration, delving into the intertwined realms of ethics, law, and technology. It underscored the importance of balancing inquisitiveness with responsibility, highlighting the delicate nature of reverse engineering. As we progress, our commitment to using our skills for the advancement of technology and its users remains steadfast.
