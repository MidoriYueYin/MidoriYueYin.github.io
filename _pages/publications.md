---
layout: page
permalink: /publications/
title: publications
description: "* denotes equal contribution. See also my <a href='/assets/pdf/cv.pdf'>CV</a>."
nav: true
nav_order: 2
---

<!-- 论文列表由 _bibliography/papers.bib 自动生成，按条目类型分组：
     @article → Journal articles；@inproceedings → Conference proceedings；
     @misc / @unpublished → Talks & posters（Zotero 里 Presentation 类型导出一般是 @misc）。
     某一类暂时没有的话，把对应的标题和那行 bibliography 删掉即可。 -->

{% include bib_search.liquid %}

<div class="publications">

<h2 class="bibliography">Journal articles</h2>
{% bibliography --query @article %}

<h2 class="bibliography">Conference proceedings</h2>
{% bibliography --query @inproceedings %}

<h2 class="bibliography">Talks &amp; posters</h2>
{% bibliography --query @misc %}
{% bibliography --query @unpublished %}

</div>
