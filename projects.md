---
layout: page
title: "Proyek Saya"
description: "Kumpulan proyek buatan saya"
date:   2021-12-08
---

<p>Kumpulan proyek buatan saya</p>

{% for project in site.projects %}

{% capture type %}
{{ project.type }}
{% endcapture %}

{% capture next_type %}
{{ project.next.type }}
{% endcapture %}

{% if forloop.first %}
 <h2>{{ type }}</h2>

 <ul>
{% endif %}

<li><a href="{{ project.link }}">{{ project.title }}</a></li>

{% if forloop.last %}
  </ul>
{% else %}
{% if type != next_type %}
  </ul>

  <h2>{{ next_type }}</h2>
  <ul>
{% endif %}
{% endif %}

{% endfor %}