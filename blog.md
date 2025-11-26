---
layout: home
title: "Blog"
permalink: /blog/
---

# Blog

Textos curtos, notícias e deambulações entre livros, escrita e rotina.

{% if site.posts.size == 0 %}
Ainda não há posts publicados — por agora, podes ler em primeiro lugar no [Substack]({{ site.author.substack }}).
{% else %}
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>  
      <small>— {{ post.date | date: "%d.%m.%Y" }}</small>
    </li>
  {% endfor %}
</ul>
{% endif %}
