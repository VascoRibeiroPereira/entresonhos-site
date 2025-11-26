---
layout: home
title: "Entre 1000 Sonhos"
---

# Entre 1000 Sonhos

Olá, eu sou o **Vasco**, escritor de Sintra.  
Gosto de ler & escrever, deambulações, fragmentos e experiências do passado, presente e futuros possíveis.

Este espaço junta tudo o que anda a nascer **entre sonhos**:
- bastidores dos meus livros,
- textos e crónicas,
- recomendações de leitura,
- novidades para quem me acompanha.

👉 **Lê textos completos e histórias em série no Substack:**  
[Entre Sonhos no Substack]({{ site.author.substack }})

👉 **Acompanha o dia a dia de leitura e escrita no Instagram:**  
[@blog_entre_sonhos]({{ site.author.instagram }})

---

## Últimos textos do blog

{% if site.posts.size == 0 %}
Ainda não há posts publicados aqui. Em breve vais conseguir ler novidades diretamente neste site.
{% else %}
<ul>
  {% for post in site.posts limit:5 %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>  
      <small>— {{ post.date | date: "%d.%m.%Y" }}</small>
    </li>
  {% endfor %}
</ul>

<p><a href="{{ '/blog/' | relative_url }}">Ver todos os posts →</a></p>
{% endif %}
