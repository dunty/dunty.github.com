---
layout: page
title: 把握当下 
---
{% include JB/setup %}

{% for post in site.posts limit:10 %}

<div style="border-style:solid; border-color:#EEE;padding:5px;padding-top:20px;-webkit-border-radius:6px;-moz-border-radius:6px;border-radius:6px;background-color: #bfa524;">
<h1 class="index-post-title">{{ post.title }}</h1> <em>posted on   {{ post.date | date_to_string }}</em>
<hr/>
{{ post.content  | strip_html | truncate: 150 }}
<p>
<a href="{{ post.url }}" style="text-align:right;" >Read More...</a>
</p>
</div>


{% endfor %}

<div style="text-align:right;">
  <a href="{{ site.JB.archive_path }}">More...</a>
</div>

    


