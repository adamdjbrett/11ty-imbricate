---
title: Blog
description: Update from my blog post
pagination:
  data: collections.posts
  size: 5
  reverse: true
testdata:
 - item1
 - item2
 - item3
 - item4
permalink: "blog/{% if pagination.pageNumber > 0 %}page-{{ pagination.pageNumber + 1 }}/{% endif %}index.html"
---
<div class="row">
{%- for post in pagination.items %}<div class="c g2">
<h3><a href="{{post.url}}">{{post.data.title}}</a></h3>
<p><time datetime="{{ post.date | htmlDateString }}">{{ post.date | readableDate("dd LLLL yyyy") }}</time></p>
<p>{{post.data.description}}</p>
<p>By <a href="{{metadata.author.url}}">{{metadata.author.name}}</a></p>
</div>{% endfor %}
</div>
<table>
<thead>
<tr>
<th class="tidak">{% if pagination.href.previous %}<a href="{{ pagination.href.previous }}" class="non s" aria-label="Previous Blog List Article">← Previous</a>{% endif %}</th>
<th class="tidak end">{% if pagination.href.next %}<a href="{{ pagination.href.next }}" class="non s" aria-label="Next Blog List Article">Next →</a>{% endif %}</th>
</tr>
</thead>
</table>
