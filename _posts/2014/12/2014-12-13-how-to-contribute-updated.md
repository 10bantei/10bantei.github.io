---
author: arukakan
comments: true
date: 2014-12-13 22:12:12+00:00
layout: post
slug: how-to-contribute
title: 投稿方法(コントリビュータ求む)
categories: Octpress
tags: Web GithubPages arukakan
---

<!-- ここまでテンプレ -->

<!-- more -->

## かんがえかた

せっかくgithubで管理するので記事募集してもいいかも。  
MITライセンス？ 

## セットアップ

必要なツールのインストール

	sudo gem install jekyll

書き始める前に必ず、他の人の編集をマージするため

	git pull

しておく。

## 記事の作成

	_posts/年/月(二桁埋め)

ディレクトリの下にmarkdownファイルを設置する。  
タグやらヘッダやらおまじないが結構あるので、  
既存のファイルをコピペして、  
"ここまでテンプレ"  
という部分までは流用する。  
(これはじゅうばんていの運用ポリシーとしてそうするだけ)

## 画像等のリソースのアップロード

img/年/月(2桁0埋め)

の下にファイルを配置すると、
a.fff.io/img/年/月/ファイル名  
でアクセス可能。

## 投稿

必ずローカルで確認してからポストすること

	jekyll server

で起動。localhost:4000にアクセスして確認。  
確認できたら、

	jekyll build
	git add -A
	git commit -m '編集内容の説明'
	git push

## テーマの反映

[ココを見て](http://jekyllbootstrap.com/usage/jekyll-theming.html)  

現状、テーマにはanalyticsとコメント欄とタイトルの下のタグ、  
あとrelated postの分を変更を追加してあるため、  
変更後のテーマにも同様の内容を追加する。  

### analytics

_includes/themes/変更したいテーマ/default.html

    <script>
      (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
      (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
      m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
      })(window,document,'script','//www.google-analytics.com/analytics.js','ga');
    
      ga('create', 'UA-57632046-1', 'auto');
      ga('send', 'pageview');
    
    </script>

### tags

_includes/themes/変更したいテーマ/post.html  

{の直後と}の直前の空白を消してから張ること

  <ul class="tag_box inline" style="list-style:none">
    { % assign tags_list = page.tags % }
    { % include JB/tags_list % }
  </ul>  
  <br/ >

### related posts

_includes/themes/変更したいテーマ/post.html  

{の直後と}の直前の空白を消してから張ること

  <h3>related posts</h3>
  <ul class="posts">
    { % for post in site.related_posts % }
      <li><span>{ { post.date | date_to_string } }</span> &raquo; <a href="{ { BASE_PATH } }{ { post  .url } }">{ { post.title } }</a></li>
    { % endfor % }
  </ul>

### comment欄

_includes/JB/comments(これはテーマ共通のため修正不要)

	<div id="disqus_thread"></div>
    <script type="text/javascript">
        /* * * CONFIGURATION VARIABLES: EDIT BEFORE PASTING INTO YOUR WEBPAGE * * */
        var disqus_shortname = 'jubantei'; // required: replace example with your forum shortname

        /* * * DON'T EDIT BELOW THIS LINE * * */
        (function() {
            var dsq = document.createElement('script'); dsq.type = 'text/javascript'; dsq.async = true;
            dsq.src = '//' + disqus_shortname + '.disqus.com/embed.js';
            (document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(dsq);
        })();
    </script>
    <noscript>Please enable JavaScript to view the <a href="http://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>


## 独自ドメイン

source/CNAME

にドメインをベタ書き。絶対消さないこと。












