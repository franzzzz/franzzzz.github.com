---
layout: page
title: 你好 旅行者
tagline: Supporting tagline
---
{% include JB/setup %}

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

---

<iframe width="100%" height="100" class="share_self"  frameborder="0" scrolling="no" src="http://widget.weibo.com/weiboshow/index.php?language=&width=0&height=550&fansRow=2&ptype=0&speed=0&skin=1&isTitle=1&noborder=0&isWeibo=0&isFans=0&uid=1352190133&verifier=6eb0bc27&dpc=1"></iframe>

---


