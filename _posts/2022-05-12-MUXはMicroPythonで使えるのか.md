---
layout: default
title: "ev3fast"
tags: ev3 ev3-micropython
---

# EV3 Sensor MultiplexerはMicroPythonで使えるのか？

## はじめに
ev3dev-python・MicroPythonについてある程度知識がある前提での記事です。<br>
ev3dev-pythonでのEV3 Sensor Multiplexerの使い方は[過去の記事](https://qiita.com/kikou0517/items/333dc18d64425c9c7857)を参照してください。<br>

「[EV3 Sensor Multiplexer](http://www.mindsensors.com/ev3-and-nxt/23-ev3-sensor-multiplexer-for-ev3-or-nxt)はMicroPythonで使えるのか？」という疑問に対するヒントが[GithubのIssues](https://github.com/pybricks/support/issues/11)にあったので紹介します。<br>※ここのIssuesではEV3 **Sensor** MultiplexerとEV3 **Motor** Multiplexerの話が混在しています。

## I2CDevice Classを使おう
このIssuesの内容を一言で端的にまとめるなら「[I2CDevice Class](https://pybricks.com/ev3-micropython/iodevices.html#i2c-device)を使おう」です。<br>
EV3 Sensor MultiplexerとEV3 Motor Multiplexerこのいずれに関してもI2Cデバイスであるため[EV3Devices Class](https://pybricks.com/ev3-micropython/ev3devices.html#module-pybricks.ev3devices)は使えないそう。<br>
また、`Ev3devSensor`はev3devでサポートされているものの使えないそう。<br>
ただし、Pybriks ver1.0では`ev3dev2.sensor.lego`の`LegoPort`Classが使えたそう。<br>

I2Cアドレスは以下の通りです。<br>
| MUXのポート | I2Cアドレス(16進法) | I2Cアドレス(10進法) |
| :-: | :-: | :-: |
| C1 | 0x50 | 80 |
| C2 | 0x51 | 81 |
| C3 | 0x52 | 82 |

今後この記事の内容を実際に試すことができたら追記しようと思います。<br>
