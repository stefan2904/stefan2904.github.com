---
layout: page
title: Home
section: home
---
{% include JB/setup %}

<ul class="posts">
  {% for post in site.posts %}
    <li>
    	<span>{{ post.date | date: "%d.%m.%Y" }}</span> &raquo;
		{% for cat in post.categories %}
			<span class="category">[{{ cat }}]</span>
		{% endfor %}
		<a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
<a href="https://github.com/stefan2904/stefan2904.github.com/commits/master">
	<small>Zuletzt aktualisiert am {{ 'now' | date: "%d.%m.%Y" }}</small>
</a>