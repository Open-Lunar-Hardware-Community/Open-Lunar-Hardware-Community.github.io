---
layout: home
title: Home
---

{% for section in site.data.sections %}
<section id="{{ section.id }}" style="padding: 40px 0; border-bottom: 1px solid #eee;">
  
  <h1 style="text-align: center;">{{ section.title }}</h1>
  {% if section.subtitle %}
    <h3 style="text-align: center; color: #666;">{{ section.subtitle }}</h3>
  {% endif %}

  {% if section.image %}
  <div style="text-align: center; margin: 20px 0;">
    <img src="{{ section.image }}" alt="{{ section.title }}" style="max-width: 80%; height: auto; border-radius: 5px;">
    {% if section.image_caption %}
      <p style="font-style: italic; color: #777;">{{ section.image_caption }}</p>
    {% endif %}
  </div>
  {% endif %}

  {% if section.content %}
    <div class="content-block">
      {{ section.content | markdownify }}
    </div>
  {% endif %}

  {% if section.lists %}
    {% for list in section.lists %}
      <h3>{{ list.title }}</h3>
      <ul>
      {% for item in list.items %}
        <li>{{ item | markdownify }}</li>
      {% endfor %}
      </ul>
    {% endfor %}
  {% endif %}

  {% if section.subsections %}
    {% for sub in section.subsections %}
      <h3>{{ sub.title }}</h3>
      {% if sub.description %}<p>{{ sub.description }}</p>{% endif %}
      <ul>
      {% for item in sub.items %}
        <li>{{ item | markdownify }}</li>
      {% endfor %}
      </ul>
    {% endfor %}
  {% endif %}

  <div style="text-align: center; margin-top: 20px;">
    {% if section.buttons %}
      {% for btn in section.buttons %}
        <a href="{{ btn.link }}" class="btn" style="margin: 0 10px; font-weight: bold;">{{ btn.text }}</a>
      {% endfor %}
    {% endif %}
    
    {% if section.links %}
      {% for link in section.links %}
        <p><a href="{{ link.url }}">{{ link.text }}</a></p>
      {% endfor %}
    {% endif %}
  </div>

</section>
{% endfor %}
