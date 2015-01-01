---
author: mizuman
comments: true
date: 2015-01-02 03:00:00+00:00
layout: article
slug: broadcast-devices
title: PS4やPS3のプレイ動画やゲーム実況に必要な機材の紹介
excerpt: PS4やPS3でゲーム実況や配信をする際に利用している機材を紹介します。
image:
  teaser: 2015/01/wirecast-400x250.png #400x250.png
categories: tech
tags: PS4 broadcast mizuman
ads: true
---

こんにちは。みずまんです。  
PS4やPS3でゲーム実況や配信をする際に利用している機材を紹介します。
機器の組み合わせは様々で、どこに配信するか、誰の声を入れるのか、
ネットワークの早さはどうかなどによって構成は変わります。
１つの構成例として参考にしていただければと思います。

<!--more-->

## 概要

ざっくりと私の配信環境の概要と機材をまとめます。

### 配信環境概要

PS4の映像とskypeの音声をミックスして、
Youtubeでライブ配信をしています。
録画はマシンスペック的にツラいため、
編集したい場合はYoutubeからDLしています。

* 目的：ゲーム実況のリアルタイム配信
* 媒体（配信サービス）：Youtube Live（ニコ生も配信可能）
* 映像：PS4及びPS3のプレイ動画
* 音声：PS4及びPS3のプレイ音声とメンバーのSkype音声
* 回線：有線でのインターネット接続（上りは10〜80Mbps）
* 録画：なし（YoutubeからMP4としてDLして利用）

### 配信機材

* ゲーム機：PS4/PS3
* 映像分配機：（PS3時のみ）HDMI Splitter
* 映像変換機：（PS3時のみ）Game Switch
* キャプチャー：Blackmagic Intensity Extreme
* ミキシング、エンコード、配信：Macbook Pro
* ソフト
  * チャット：Skype（無料）
  * 配信：wirecast for Youtube（無料）
  * 仮想音源：Soundflower（無料）
  * 仮想ミキサー：LadioCast（無料）

### 構成

ざっくりと構成はこんな感じです

<figure>
  <img src="/images/2015/01/rec-configuration.jpg">
</figure>

## ポイント

詳細な配信方法やチャンネルの作成方法は別途まとめますが、
詰まりやすいポイントを先に書いておきます。

### PS4単体でのゲーム実況の配信

PS4（とXbox One）は素晴らしく、本体だけでゲーム実況が可能です。
配信機材は非常に高価であり、また機器の相性や配線、セッティングの手間、著作権の問題もあるため、本体の機能で配信してしまうことをオススメします。  
ただし、私が配信機材を利用しているのにも理由があります。
以下に注意してください。

* 2015年1月2日現在、ニコ生、Ustream、Twitchでの
リアルタイム配信に対応していますが、Youtubeは録画した動画のアップロードのみで、リアルタイムでの配信はできません。  
* 録画時に動画は圧縮されてしまうため、Youtubeでの高画質配信にはむきません。また、録画は30分で終了します。

### PS4の映像がキャプチャーできない

どのような構成であれ、一番ハマりやすいのはこれです。  
いくつか考えられる原因はありますが、まずは検討すべきなのが、
解像度とフレームレートの不一致です。

* 映像を出力するPS4とキャプチャデバイスの入力の解像度とフレームレートが合っていない
* キャプチャデバイスの出力と配信ソフトの入力の解像度とフレームレートが合っていない

映像を受け止める側が自動的に認識して処理することができればいいのですが、
優しくない機器が多いです。

そこで、PS4の出力、キャプチャデバイスの入力と出力、
配信ソフトの入力を全て統一するのがオススメです。  
私はキャプチャデバイスの性能、エンコードするMacbook Proの処理能力とアップロード回線を考慮して、
解像度は720p、フレームレートは59.94fpsにしています。

1. PS4の映像出力を720pにする  
![PS4映像出力設定画面](/images/2015/01/PS4-display-config.jpg "PS4映像出力設定画面")

1. キャプチャデバイスの設定を720p59.94fpsにする  
![キャプチャデバイス設定画面](/images/2015/01/capture-config.png "キャプチャデバイス設定画面")

1. 配信ソフトの入力設定を720p59.94fpsにする
![配信ソフト設定画面](/images/2015/01/wirecast-config.png "配信ソフト設定画面")

1. 配信ソフトで表示されることを確認する
![配信画面](/images/2015/01/wirecast.png "配信画面")

※よく60fpsと言われますが、だいたい59.94fpsです。  
※配信ソフトがキャプチャデバイスの認識に失敗していることもあるため、配信ソフトの再起動も試してみてください。  
※PS3の場合、HDCPによりHDMI出力をそのままキャプチャできません。

### 配信がカクカクする

ゲームは通常通りプレイできているのに、配信ではフレームレートが安定せずにカクつくことがあります。  
その理由として、以下の3点がまず考えられます。

1. エンコードの処理速度不足
1. アップロードの回線速度不足
1. 配信サービスのビットレート制限

#### エンコードの処理速度不足

WindowsやMacの処理速度が追いつかずに、フレームレートが不安定になるパターンです。  
FMLE(Adobe Flash Media Live Encoder)など重いエンコーダーを利用していたり、
1080pから720p、60fpsから30fpsなど変換処理を加えると負荷が高くなり、発生しやすくなります。  
配信を720pで行う場合は、PS4も720pでの出力にするなど、負荷を減らす工夫ができます。

#### アップロードの回線速度不足

高解像度、高フレームレートの動画のアップロードには、
安定した高速な回線が必要です。  
速度が出ていれば問題ないということではないですが、
配信前に回線速度測定サイトで計測し、下記のリストを参考にしてください。

* 1080p : 3-6Mbps
* 720p : 1.5-4Mbps
* 480p : 500kbps-2Mbps

#### 配信サービスのビットレート制限

各動画配信サービスには、動画のビットレート制限があります。
別の記事でまとめます。