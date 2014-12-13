---
author: arukakan
comments: true
date: 2014-12-13 00:12:12+00:00
layout: post
slug: how-to-contribute
title: 投稿方法(Octopressの方法)
categories: Octpress
tags: Octpress Web GithubPages arukakan さぎにゃん
---

[jekyllに移行したので、管理は別になりました。](/2014/12/13/how-to-contribute-updated)

## かんがえかた

せっかくgithubで管理するので記事募集してもいいかも。  
MITライセンス？ 

## セットアップ

書き始める前に必ず、他の人の編集をマージするため

	git pull

しておく。

## 記事の作成

	_posts/年/月(二桁埋め)

ディレクトリの下にmarkdownファイルを設置する。  
(これはじゅうばんていの運用ポリシーとしてそうするだけ)

markdownを編集したら、

	git add -A
	git commit -m '編集内容の説明'
	git push

## 画像等のリソースのアップロード

img/年/月(2桁0埋め)

の下にファイルを配置すると、
a.fff.io/img/年/月/ファイル名  
でアクセス可能。

## テーマの反映

[ココを見て](http://jekyllbootstrap.com/usage/jekyll-theming.html)

## 独自ドメイン

source/CNAME

にドメインをベタ書き。絶対消さないこと。






