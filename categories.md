---
layout: archive
permalink: /categories.html
title: "Categories"
excerpt: げーむとぎじゅつのむだづかい。ゲームに関する情報や配信をしながら、ゲームに便利なツールなども提供していきます。
meta_keywords: game, ゲーム, 攻略, ツール, 配信
---
{% include JB/setup %}

<ul class="tag_box inline">
  {% assign categories_list = site.categories %}
  {% include JB/categories_list %}
</ul>

<div style="clear:both;"></div>

{% for category in site.categories %} 
  <h2 id="{{ category[0] }}-ref">{{ category[0] | join: "/" }}</h2>
  <ul>
    {% assign pages_list = category[1] %}  
    {% include JB/pages_list %}
  </ul>
{% endfor %}