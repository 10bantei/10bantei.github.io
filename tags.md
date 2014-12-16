---
layout: archive
permalink: /tags.html
title: "Tag"
excerpt: げーむとぎじゅつのむだづかい。ゲームに関する情報や配信をしながら、ゲームに便利なツールなども提供していきます。
meta_keywords: game, ゲーム, 攻略, ツール, 配信
---
{% include JB/setup %}

<ul class="tag_box inline">
{% assign tags_list = site.tags %}  
{% include JB/tags_list %}
</ul>

<div style="clear:both;"></div>

{% for tag in site.tags %} 
<h2 id="{{ tag[0] }}-ref">{{ tag[0] }}</h2>
<ul>
{% assign pages_list = tag[1] %}  
{% include JB/pages_list %}
</ul>
{% endfor %}