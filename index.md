---
layout: home
title: "Entre Sonhos"
---

<span class="hero-tag">entre sonhos</span>

# Entre Sonhos

Olá, eu sou o **Vasco**, escritor de Sintra.  
Gosto de ler & escrever, deambulações, fragmentos e experiências do passado, presente e futuros possíveis.

O **Entre Sonhos** é o meu ponto de encontro contigo:
- bastidores dos livros em que estou a trabalhar,
- textos e crónicas,
- recomendações de leitura,
- notícias e pequenas novidades para quem gosta de acompanhar o processo.

👉 **Textos completos, capítulos e histórias em série:**  
[Entre Sonhos no Substack]({{ site.author.substack }})

👉 **Bastidores de leitura e escrita no dia a dia:**  
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
