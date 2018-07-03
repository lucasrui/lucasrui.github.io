---
title: Category 
layout: default
---


<div class="g-banner tags-banner {{ site.postPatterns | prepend: 'post-pattern-' }} {{ site.theme-color | prepend: 'bgcolor-' }}" data-theme="{{ site.theme-color }}">
    <h2>CATEGORY</h2>
</div>

<div style="background: #F7F6F6;">
	
{% for category in site.categories %}

<p style="font-size:24px;margin-left:5%;">
<i class="fa fa-folder"></i>
<a href="#{{ category | first }}" title="view all posts in &lt;{{ category | first }}&gt;">

{{ category | first }}

</a>
<i class="fa fa-angle-left"></i>

{{ category | last | size }}

<i class="fa fa-angle-right"></i></p>

{% endfor %}

</div>
<h2 style="text-align:center;">
<i class="fa fa-bolt"></i>
<i class="fa fa-bolt"></i>
<i class="fa fa-bolt"></i>
<strong>
Details
</strong></h2>

{% for category in site.categories %}

<p style="font-size:24px;margin-left:5%;">

<i class="fa fa-folder-open"></i>

<a href="#{{ category | first }}" name="{{ category | first }}" title="view all posts in &lt;{{ category | first }}&gt;">

{{ category | first }}

</a>
<i class="fa fa-angle-left"></i>

{{ category | last | size }}

<i class="fa fa-angle-right"></i></p>
<ul>

{% for post in category.last %}

<ol>
<i class="fa fa-calendar"></i>

{{ post.date | date:"%Y-%m-%d"}}

<i class="fa fa-terminal"></i>
<a href="{{ post.url }}">

{{ post.title }}

</a></ol>

{% endfor %}

</ul> 

{% endfor %}
