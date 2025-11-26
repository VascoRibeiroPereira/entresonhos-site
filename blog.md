---
layout: page
title: "Blog"
permalink: /blog/
---


Textos curtos, notícias e deambulações entre livros, escrita e rotina.

Neste momento, a maior parte dos textos vive no Substack:

👉 [Entre Sonhos no Substack]({{ site.substack }})

---

## Posts aqui no site

{% if site.posts.size == 0 %}
Ainda não há posts publicados diretamente aqui no site — por agora, podes ler em primeiro lugar no [Substack]({{ site.substack }}).
{% else %}
<ul class="post-list">
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>  
      <small>— {{ post.date | date: "%d.%m.%Y" }}</small>
    </li>
  {% endfor %}
</ul>
{% endif %}
