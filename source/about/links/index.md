---
title: 友链
date: 2022-01-05 19:04:33
type: "links"
comments: false
---

![友链封面](https://gitee.com/josephucas/pcc-beed/raw/master/img/202201061020563.webp)

<div class="links-content">
<div class="no-icon note warning"><div class="link-info">😁欢迎与我交换友链</div></div>
<div class="link-navigation">
{% for link in site.data.links.defaultlinks %}
<div class="card">
<img class="ava nomediumzoom" src="{{ link.avatar }}"/>
<div class="card-header">
<div><a href="{{ link.site }}" target="_blank"> {{ link.name }}</a> </div>
<div class="info">{{ link.info }}</div>
</div>
</div>
{% endfor %}
</div>

------

<div style="text-align:center;"><span class="with-love" id="animate1">
    <i class="fa fa-heart"></i>
  </span>留言添加友链<span class="with-love" id="animate2">
    <i class="fa fa-heart"></i>
  </span></div>

------

{% note success %}

**友链格式：**

- 网站名称：他乡之客
- 网站地址：https://josephucas.github.io/
- 网站描述：凡有所学，皆成性格
- 网站Logo/头像：https://josephucas.github.io/images/avatar.jpg

{% endnote %}

