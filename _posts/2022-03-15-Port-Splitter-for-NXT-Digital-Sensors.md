---
layout: default
title: "EV3のポートを増やしたい ~Port Splitter for NXT Digital Sensors~ with Python"
tags: ev3 ev3dev-python
---
# EV3のポートを増やしたい ~Port Splitter for NXT Digital Sensors~ with Python

# Introduction / はじめに
There are some way to increase the number of EV3's ports.<br>
[__Port Splitter for NXT Digital Sensors__](http://www.mindsensors.com/ev3-and-nxt/52-port-splitter-for-nxt-digital-sensors) is one of them.<br>
I would like to introduce how to use it with __Python__(ev3dev).<br>

[__Port Splitter for NXT Digital Sensors__](http://www.mindsensors.com/ev3-and-nxt/52-port-splitter-for-nxt-digital-sensors)はEV3のセンサーの数を増やす方法の１つです。ここではPort SplitterをPython(ev3dev)で使う方法について紹介します。<br>
<br>
<img width="300" alt="port-splitter-for-nxt-digital-sensors.jpg" src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2449798/a7b0b21f-008a-5809-232a-e5fd378ef689.jpeg">

# How to use sensors/ 使い方
We use __I2C__ to connecte sensors or motors; thus you can use only I2C sensors.(For example you can not use EV3 color sensor)<br>
Sensor which you can use with "Port Splitter" are shown in the list below and I2C sosnors of the list of [this link](https://docs.ev3dev.org/projects/lego-linux-drivers/en/ev3dev-jessie/sensors.html).<br>

|                                                                      |                                         | 
| :------------------------------------------------------------------: | :-------------------------------------: | 
| Vision Subsystem v4 for NXT or EV3                               | NXTCam-v4 (and all older models)        | 
| LEGO NXT Ultrasonic Sensor                                           | (only one can be used)                  | 
| GlideWheel-AS - Angle Sensor for NXT or EV3                          | GlideWheel-AS                           | 
| Sony PlayStation 2 Controller interface for NXT or EV3               | PSP-Nx-v4-c & PSP-Nx-v4-REF             | 
| Digital Pneumatic Pressure Sensor for NXT or EV3                     | PPS58-Nx                                | 
| Light Sensor Array                                                   | LightSensorArray                        | 
| Line Follower Sensor for NXT or EV3                                  | LineLeader-v2 (as well as older models) | 
| High Precision Infrared distance sensors for NXT or EV3 (all models) | DIST-NxL-v3, DIST-NxM-v3, DIST-NxS-v3   | 
| VoltMeter for NXT or EV3                                             | NXTVoltMeter                            | 
| CurrentMeter for NXT or EV3                                          | NXTCurrentMeter                         | 
| Gyro, MultiSensitivity Accelerometer and Compass for NXT or EV3      | AbsoluteIMU-ACG                         | 
| MultiSensitivity Accelerometer and Compass for NXT or EV3            | AbsoluteIMU-AC                          | 
| Multi-Sensitivity Acceleration Sensor for NXT or EV3                 | AbsoluteIMU-A                           | 
| Compass for NXT or EV3                                               | AbsoluteIMU-C                           | 
| 8 Channel Servo Controller for NXT or EV3                            | NXTServo-v3 & NXTServo-v2               | 
| Multiplexer for NXT Motors                                           | NXTMMX - All models                     | 
| Sensor Kits with PCF8574 and PCF8591 ICs.                            |                                         | 
| PF Motor Controller                                                  | PFMate                                  | 
| EV3 Sensor Adapter for NXT or Arduino                                | EV3SensorAdapter                        | 
| IR Temperature Sensor fot EV3                                        | 	IRThermometer                          | 
| HiTechnic or Dexter I2C (Digital) devices                            | (must have unique i2c address)          | 

接続にはI2Cアドレスを使用します。Port SplitterにはI2Cセンサーのみ使用できます。(例えば、EV3カラーセンサーは使えません)使えるセンサーについては上の表もしくは[このリンク](https://docs.ev3dev.org/projects/lego-linux-drivers/en/ev3dev-jessie/sensors.html)のI2Cセンサーから見ることができます。<br>

You can find I2C-addresses [here](https://docs.ev3dev.org/projects/lego-linux-drivers/en/ev3dev-jessie/i2c.html#useful-info).  <br>
The actual address used in the program is in the basic form `in<n>:i2c<m>`<br>
\<n> is the port number of EV3 which Port Splitter is connected.<br>
\<m> is I2C-address of decimal number of your sensor<br>

You can address like this code.
```
colorsensor = ColorSensor("in1:i2c1")
```

I2Cアドレスは[ここ](https://docs.ev3dev.org/projects/lego-linux-drivers/en/ev3dev-jessie/i2c.html#useful-info)から探せます。<br>
実際にプログラムで使うアドレスのフォーマットは`in<n>:i2c<m>`です。<br>
\<n>はPort Splitterが接続されているEV3のポート番号です。<br>
\<m>はセンサーのアドレス(10進数)です。<br>
アドレスは上記のサンプルコードのように指定します。<br>

# How to use Motors / モーターについて
You can also use motors, however you can not control an independent motor.<br>
__You can only run all motors at once.__<br>

モータを使うことはできます。ですが、すべてのモータを一度に動かすことのみ可能で、__個別に操作することはできません__。<br>

# Disclaimer / 免責
__This blog may not be based on right information, because it is inadequately validated...<br>
I can not be held responsible for this blog!<br>
Please use it at your own risk.__<br>

この記事の内容は検証が不十分なので正しい情報でない可能性があります。<br>
また、私はこの記事の内容について一切の責任を負いかねます。<br>
自己責任でご利用ください。<br>

# References
[https://docs.ev3dev.org/projects/lego-linux-drivers/en/ev3dev-jessie/muxs.html#port-splitter-for-nxt-digital-sensors](https://docs.ev3dev.org/projects/lego-linux-drivers/en/ev3dev-jessie/muxs.html#port-splitter-for-nxt-digital-sensors)

[http://www.mindsensors.com/ev3-and-nxt/52-port-splitter-for-nxt-digital-sensors](http://www.mindsensors.com/ev3-and-nxt/52-port-splitter-for-nxt-digital-sensors)

[https://ev3dev-lang.readthedocs.io/projects/python-ev3dev/en/latest/index.htmlz](https://ev3dev-lang.readthedocs.io/projects/python-ev3dev/en/latest/index.htmlz)
