---
title: "Home"
layout: homelay
sitemap: false
permalink: /
---

<h2 class="home-hero">{{ site.name }}</h2>
<p class="home-hero-sub">{{ site.title }}, {{ site.institution }}</p>

### About me

Dr. Huadong Zeng is a Lecturer in the College of Materials and New Energy at [South China Normal University](https://www.scnu.edu.cn/). He received his Ph.D. degree from Sichuan University.

His research focuses on computational materials science and theoretical design of novel functional and energy materials. His main research directions include:
1. **Carrier Dynamics**: Excited-state carrier dynamics in novel functional materials (such as 2D materials and heterostructures).
2. **Energetic Materials**: Structural design and reaction behavior of (smart) controllable energetic materials.
3. **Hydrogen Storage & Energy Materials**: Theoretical prediction and physicochemical property studies of novel energy (hydrogen storage) materials.
4. **Battery Materials Design**: Molecular design of 2D functional materials for battery applications.

<div class="chip-container" markdown="0">
<a href="{{ site.url }}{{ site.baseurl }}/research" class="chip">Carrier Dynamics</a>
<a href="{{ site.url }}{{ site.baseurl }}/research" class="chip">2D Materials & Heterostructures</a>
<a href="{{ site.url }}{{ site.baseurl }}/research" class="chip">Energetic Materials</a>
<a href="{{ site.url }}{{ site.baseurl }}/research" class="chip">Hydrogen Storage</a>
<a href="{{ site.url }}{{ site.baseurl }}/research" class="chip">Battery Materials Design</a>
</div>

### Recent Research

{% assign sorted_research = site.data.web.research | sort: "end_date" | reverse %}
<div class="home-projects-grid" markdown="0">
{% for item in sorted_research limit:4 %}
{% assign card_id = item.title | slugify %}
<a href="{{ site.url }}{{ site.baseurl }}/research#{{ card_id }}" class="home-project-card">
{% if item.image and item.image != "" %}
<img src="{{ site.url }}{{ site.baseurl }}/images/{{ item.image }}" alt="{{ item.title }}" loading="lazy">
{% endif %}
<div class="home-project-card-body">
<h4>{{ item.title }}</h4>
<p>{{ item.abstract | truncatewords: 20 }}</p>
</div>
</a>
{% endfor %}
</div>

{% if site.data.web.projects and site.data.web.projects.size > 0 %}
### Software I've Built

{% assign sorted_projects = site.data.web.projects | sort: "end_date" | reverse %}
<div class="home-software-list" markdown="0">
{% for item in sorted_projects limit:2 %}
{% assign card_id = item.title | slugify %}
<a href="{{ site.url }}{{ site.baseurl }}/projects#{{ card_id }}" class="home-software-card">
{% if item.image and item.image != "" %}
<div class="home-software-card-media">
<img src="{{ site.url }}{{ site.baseurl }}/images/{{ item.image }}" alt="{{ item.title }}" loading="lazy">
</div>
{% endif %}
<div class="home-software-card-body">
<h4>{{ item.title }}</h4>
{% if item.status or item.role or item.start_date %}
<div class="home-software-meta">
{% if item.status and item.status != "" %}<span class="home-software-status">{{ item.status }}</span>{% endif %}
{% if item.role and item.role != "" %}<span>{{ item.role }}</span>{% endif %}
{% if item.start_date %}<span>{{ item.start_date }}{% if item.end_date %}&ndash;{{ item.end_date }}{% else %}&ndash;Present{% endif %}</span>{% endif %}
</div>
{% endif %}
<p>{{ item.abstract | truncatewords: 42 }}</p>
{% if item.stack %}
<div class="home-software-stack">
{% for tech in item.stack limit:6 %}<span>{{ tech }}</span>{% endfor %}{% if item.stack.size > 6 %}<span>+{{ item.stack.size | minus: 6 }} more</span>{% endif %}
</div>
{% endif %}
<div class="home-software-cta">View project <i class="fa-solid fa-arrow-right"></i></div>
</div>
</a>
{% endfor %}
</div>

<p style="margin-top: var(--space-4);"><a href="{{ site.url }}{{ site.baseurl }}/projects">See all projects &rarr;</a></p>
{% endif %}