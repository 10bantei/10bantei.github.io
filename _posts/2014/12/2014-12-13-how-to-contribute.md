---
author: arukakan
comments: true
date: 2014-12-13 00:12:12+00:00
layout: post
slug: how-to-contribute
title: 投稿方法(Octopressの方法)
categories: Octpress
tags: Octpress Web GithubPages arukakan
---

<!-- more -->
  <ul class="tag_box inline" style="list-style:none">
    {% assign tags_list = page.tags %}
    {% include JB/tags_list %}
  </ul>
  <br/ >

<!-- ここまでテンプレ -->

[jekyllに移行したので、管理は別になりました。](/2014/12/13/how-to-contribute-updated)

## かんがえかた

せっかくgithubで管理するので記事募集してもいいかも。  
MITライセンス？ 

## ブランチの構成

master: 記事本体。スタティックなWebサイト  
source: markdownファイルやその他の原稿ファイル

なので、記事作成の際にはsourceを編集し、  
masterをoctpressの機能で生成 & deployすることになる。

	git clone git@github.com:10bantei/10bantei.github.io.git	
	git fetch origin source
	git checkout -f source

して、sourceを準備する。  
git fetchではなくpullしてしまうとマージしようとして面倒。  
そもそもsourceとmasterは別概念なのでマージできない。

## セットアップ

octopressがgemをいっぱい呼ぶので、

	bundle install

しておく。

## 記事の作成

__前の人との差分をつめるために、書き始める前に必ずgit fetchすること。__

	rake new_post\["how to contribute"\] #zshの場合

もしくは

	rake new_post["how to contribute"] #その他のシェルの場合

でsouces/_posts/直下にmarkdownファイルが生成される。  
今後の整理のため、年/月(2桁埋め)というディレクトリを生成し、  
その下に移動する。(これはじゅうばんていの運用ポリシーとしてそうするだけ)

markdownを編集したら、

	rake setup_github_pages

を行う。  
最初に適用先リポジトリを求められるので、  

	git@github.com:10bantei/10bantei.github.io.git

を与える。その他の選択肢はすべてno。
その後

	rake preview

で動作確認後、

	rake genarate
	rake deploy

すれば記事がアップロードされる。  
反映までにgithub内で処理があるので10分程度かかる模様。	  
このままだとブログがmasterにpushされているだけなので、  
原稿の方もpushしておく。  

	git add -A
	git commit -m '編集内容の説明'
	git push origin source 

## 画像等のリソースのアップロード

source/img/年/月(2桁0埋め)

の下にファイルを配置すると、
a.fff.io/img/年/月/ファイル名  
でアクセス可能。

## テーマの反映

[https://github.com/imathis/octopress/wiki/3rd-Party-Octopress-Themes](https://github.com/imathis/octopress/wiki/3rd-Party-Octopress-Themes)

からカッコイイテーマを選択し、githubのリポジトリへ飛ぶ。  
大概説明が書いてあるが、たとえばoctograyの場合

	$ git submodule add git@github.com:rcmdnk/octogray.git .themes/octogray
	$ .themes/octogray/setup.sh
	$ rake setup_github_pages

whitespaceの場合

	$ git clone git://github.com/lucaslew/whitespace.git .themes/whitespace
	$ rake install['whitespace'] # for zsh, use: rake install\['whitespace'\]
	$ rake generate

## 独自ドメイン

source/CNAME

にドメインをベタ書き。絶対消さないこと。

## メモ

なんかページ全体が変なリンク状態。  
octograyの機能がバグってるっぽいので後で確認  
or  
別のテーマに変更


