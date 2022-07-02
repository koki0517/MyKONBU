---
layout: default
title: "LEGO SPIKE Primeでデイジーチェーン(Hub to Hub communication)"
tags: spike-prime
---

# LEGO SPIKE Primeでデイジーチェーン(Hub to Hub communication)

## はじめに
EV3には本体同士を接続してポート数を増やす「デイジーチェーン(Daisy Chain)」という機能がありました。残念ながらこれに相当する機能は2022年5/2時点で**SPIKE Primeにはありません**。<br>
しかし、[Robot Inventor 51515](https://www.lego.com/ja-jp/product/robot-inventor-51515)にはハブ間での通信を可能にする「**Hub to Hub communication**」という機能があります。<br>
Robot Inventor 51515はハードウェア的にはSPIKE Primeと全く同じ(色は緑色の)製品です。残念ながら現在日本での正規代理店からの販売はありません。~~ただし、2022年の6月から日本でも販売が始まるそうです。~~[販売が始まりました](https://www.lego.com/ja-jp/product/robot-inventor-51515)。<br>

<img width="800" alt="ファイル名" src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2449798/704bac4f-bce7-6d7f-1e5c-029e6f34e73b.png">

## SPIKE PrimeをRobot Inventorに変身させる
※Robot Inventorをお持ちの方は*方法の5*まで飛ばしてください。<br>
先述の通りRobot Inventorは色が違うだけでSPIKE Primeとハードウェア的はに全く同じ製品です。<br>
つまり、**ソフトウェア-HubOSをRobot Inventorのものに書き換えてしまえば、それはRobot Inventor**なのです。<br>

### 方法
1.  まずはマインドストームのアプリをインストールします。※日本語非対応です。<br>
Windows: https://www.microsoft.com/ja-jp/p/lego-mindstorms-robot-inventor/9mtq0n7w1d6x?activetab=pivot:overviewtab <br>
Android: https://play.google.com/store/apps/details?id=com.lego.retail.mindstorms <br>
iOS&Mac: https://apps.apple.com/jp/app/lego-mindstorms-inventor/id1515448947<br>

2. SPIKE Primeを接続します。
2. HubOSを更新するというメッセージが表示されます。ボタンを押して更新しましょう。更新には少し時間がかかります。<br>※この段階でHub内のプログラムなどが消去されるかもしれないので気をつけてください。<br>
2. HubOSの更新が終わると、モータの更新画面が表示されます。<br>
2. プログラム画面左下の＋から「HUB TO HUB COMMUNICATION」を追加(ADD)する。

<img width="500" alt="ファイル名" src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2449798/4b36840d-f0ee-cd78-b291-2140c474555f.png">

<img width="600" alt="ファイル名" src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2449798/76b32786-0460-6fcb-2e2c-379ad3a206d9.png">

2. するとブロック一覧の一番下に以下の写真のようなものが追加されたら完了です。<br>

<img width="500" src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2449798/15751c6e-471b-12a9-5c63-9bafb2f49352.png">

## 使い方
※MindstormsアプリのHelpをそのまま和訳しています。いくらか間違いがあるかもしれません。<br>

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2449798/8dc70512-3656-356e-fff0-5615280a2a5a.png)

## デイジーチェーンとの違い
* デイジーチェーンは母機となるEV3が他のEV3を制御する形なのでプログラムも1台分用意すればよかったのに対して、1つ1つのHubはHub to Hubにおいてあくまでも独立しており、あるHubの発信した信号を他のHubが読み取る方法であるため、プログラムはHubの数だけ必要になります。<br>

* デイジーチェーンはUSB接続やBluetooth接続で互いを認識する必要がありました、ですがHub to Hubにおいて、あるHubの発信した信号はそのの名前さえわかれば誰のどのHubでも読み取ることができます。<br>
* 信号に載せて送ることのできる情報は変数などの値に限られるため、デイジーチェーンのように他のHubを柔軟に容易に制御することは難しくなります。<br>
* デイジーチェーンは最大4台まで接続が可能でしたが、Hub to Hubでは理論上無限のHubと通信をすることができます。<br>

## 注意点
* Hub to HubはEV3のデイジーチェーンとは違い、ハブ間でお互いを認識する必要がなく、発信された信号はどのハブでも受け取ることができます。つまり、同じ名前の信号を使っているチームが近くにいた場合、違うチームのハブからの信号を受け取ってしまいます。信号の名前を被りにくいものにする(例えば末尾に数字を付ける)ことが必須です。<br>

* Hub to HubにはBluetoothのみを使うことができ、USBは恐らく使えません。ロボカップジュニアのように無線通信の一切を禁じている大会ではHub to Hubの使用が制限されるかもしれません。実際にEV3においてデイジーチェーンをBluetoothで行うことは禁じられています。<br>
※ブロックによってはデイジーチェーンでの通信を禁止されないところもあります。本来禁止されないといけないんですけどね…<br>

## 参考文献
[https://nxt.typepad.jp/robojoy/2021/09/mindstorms51515.html](https://nxt.typepad.jp/robojoy/2021/09/mindstorms51515.html)

[https://youtu.be/47cTxxz1TQg](https://youtu.be/47cTxxz1TQg)

[https://youtu.be/Mq_mLQF1dZ4](https://youtu.be/Mq_mLQF1dZ4)
