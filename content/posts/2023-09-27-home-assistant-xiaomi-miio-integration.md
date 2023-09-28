---
title: Home Assistant's Xiaomi Miio integration
date: 2023-09-27T08:57:59+08:00
---

[Xiaomi Miio](https://www.home-assistant.io/integrations/xiaomi_miio) is an integration for [Home Assistant](https://www.home-assistant.io), an open-source home automation software. It is the link between Home Assistant itself, and your Xiaomi smart devices.

Except I don't want my network traffic routed to some server up in China or wherever when I'm at home, and the device itself is at home, as it makes for a meaningfully longer turnaround time, and is probably a privacy hole too. (The next step is cutting off "phone home" traffic from these devices, but story for another day.)

I have 6 of these smart devices, 2 of which are air purifiers of the same model (ID). Unfortunately, only the vacuum is supported out of the box, and I really wanted to be able to manage my air purifiers via Home Assistant.

At the "unsupported model" dialog, I tried using instead the Model ID listed in the rightmost table column below, and it worked; e.g.,

![Air purifier controls](/2023-09-27-xiaomi-miio-zhimi-airp-va2.png)

I'll probably continue exploring alternative model IDs, but just the air purifiers for now:

|Name|Model ID|Alt. Model ID
|-|-|-
|米家IH电饭煲|`chunmi.cooker.normal2`|?
|叮零智能视频门铃S|`madv.cateye.dlowlplus`|?
|石头扫地机器人S5|`roborock.vacuum.s5`|Not needed
|米家恒温电水壶|`yunmi.kettle.v1`|?
|米家空气净化器 4 Pro|`zhimi.airp.va2`|`zhimi.airp.vb4`
