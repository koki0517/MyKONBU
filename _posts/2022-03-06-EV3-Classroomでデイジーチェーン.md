---
layout: default
title: "EV3 classroomでデイジーチェーン"
tags: ev3
---

# EV3 classroomでデイジーチェーン（daisy chain）

## デイジーチェンとは…
EV3本体を2個つなぐことで、ポート数を増やすこと。


## 方法
1.USBでEV3本体どうしを接続する。(4台まで、Bluetooth,Wifiでできる可能性あり)<br>
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2449798/bac12bd7-e2b2-9bfd-0423-1b92016a8e65.png)<br>
2.レイヤー番号"1"のEV3をPCに接続(レイヤー番号は上の写真の左から1,2,3,4)<br>
3.ポートの指定には変数を使います。公式は"**レイヤー番号×100＋ポート番号**"<br>
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2449798/0cab7e49-dcaf-8b17-64fe-55af50be8f91.png)<br>


## 注意
- モーターのポートの番号はA→1, B→2, C→3, D→4<br>
- 移動ブロックで使用できるモーターは、1層につき1組のみ<br>
- 移動ブロックの場合、右側のモーターポートに変数を追加するだけ<br>


## 使ってみた感想
教育版EV3ソフトウェアだと、どのレイヤーにどんなセンサーないしモーターが繋がっていて、どんな値なのかを随時確認できる。だが、Classroomだとそれができないのだ。<br>
プログラムをする側からするとこれはかなり痛い。<br>
つまるところ、デイジーチェーンを使いたければClassroomではなく、教育版EV3ソフトウェアを使うのが無難だろう。また、[Multiplexer](http://www.mindsensors.com/ev3-and-nxt/23-ev3-sensor-multiplexer-for-ev3-or-nxt)を使うのも１つの手だろう。<br>


## 参考文献:
[https://ev3lessons.com/en/ProgrammingLessons/advanced/scratch-DaisyChain.pdf](https://ev3lessons.com/en/ProgrammingLessons/advanced/scratch-DaisyChain.pdf)<br>
[https://afrel.co.jp/archives/22929](https://afrel.co.jp/archives/22929)<br>
