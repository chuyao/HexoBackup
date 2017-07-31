---
title: (译) 解决Nexus5X手机死循环启动问题，帮助你最终启动手机
date: 2017-07-31 14:22:18
tags: 
    - Translation
    - Android
    - Tech
---
##### <center>*原文[《Nexus 5X Bootloop Fix Helps you to Finally Boot the Phone》][1]，源自 [xdadevelopers.com][2]网站，原文作者：[Doug Lynch][3]*</center>
&#8195;&#8195;你的LG/Google [Nexus 5X][4]手机停止启动了吗？或者是陷入到了无休止的启动循环里了？
&#8195;&#8195;这种现象我们常称之为“循环启动”，起因则有很多种。大多数时候，可以通过刷入原厂固件或者恢复出厂设置来解决循环启动问题，但当遇到硬件循环启动时，通常我们并不能采取什么有效的办法，除了退货。如果你的Google Nexus 5X手机无法启动，而你尝试修复但并没有什么卵用，那么你要相信，你不是唯一一个碰到这种情况的人。Nexus 5X循环启动问题在社区里正不断被诟病，但鲜有新的解决方案。
### Nexus 5X循环启动解决 - 背景
&#8195;&#8195;过去几年里，LG旗下的智能手机在循环启动问题上有点名声。其中一个问题，起初只在[LG G4][5]手机上发现的问题正越来越多的出现在它发布的每一款新设备上。社区里最近在讨论*[解决Nexus 6P循环启动问题][6]*，这个设备由华为出品，而现在，一个在[Nexus 5X][7]上可行的办法出现了，这个办法派生自我们之前写的一些引导方案。
&#8195;&#8195;这些解决方案有一个共同点，正表明由高通仓促发布的骁龙808/810芯片，随着使用时间的推移，正在达到退化并损坏的时候了。*[骁龙810发热问题][8]*都已经老生常谈了，但是，似乎808芯片也存在相同的问题，将导致设备循环启动。LG起初承认了*[LG G4循环启动问题确实和硬件有关][9]*，但从未提供更多深入的信息。
一些质疑认为是焊锡的问题，在设备的使用过程中，在经历多次的加热和冷却后，焊锡会破裂。不管是否是真因，我们还是不知道问题的背后是什么，但是这个办法看起来会对Nexus 5X循环启动的问题起效。今天我们带来一个引导，真正的帮助你解决Nexus 5X循环启动问题。这则帖子末尾的讨论链接表明这个办法是未经测试的，社区里的许多用户已经报告了用这个办法可以成功。
&#8195;&#8195;一如既往，你可以使这个方法多样化。
### 教程
###### 要求
* *设备在循环启动问题发生前，bootloader要处于"可解锁"状态。在这之前，如果你能启动设备，去到开发者选项里，点击“允许OEM解锁”，就能达到bootloader解锁的状态。*
1. 下载最新的[ADB和Fastboot文件][10]，将它们解压到你电脑上容易访问到的位置。
2. 下载安装[谷歌USB驱动][11] (针对windows平台)
3. 下载[N2G47Z_4Cores.img]文件，保存到与ADB&Fastboot相同的目录下。




[1]: https://www.xda-developers.com/nexus-5x-bootloop-fix-boot-phone/
[2]: https://www.xda-developers.com/
[3]: https://www.xda-developers.com/author/doug-lynch/
[4]: https://forum.xda-developers.com/nexus-5x
[5]: https://forum.xda-developers.com/g4
[6]: https://www.xda-developers.com/nexus-6p-bootloop-fix/
[7]: https://forum.xda-developers.com/nexus-5x
[8]: https://www.xda-developers.com/opinion-the-810-held-back-a-generation-with-deliberate-apologism-damage-control/
[9]: https://www.xda-developers.com/xda-external-link/lg-admits-g4-bootloop-problem-is-a-hardware-fault-will-repair-affected-devices/
[10]: https://www.xda-developers.com/google-releases-separate-adb-and-fastboot-binary-downloads/
[11]: https://developer.android.com/studio/run/win-usb.html
[12]: https://www.dropbox.com/s/tm7qt98r6d7q2a6/N2G47Z_4Cores.img?dl=0