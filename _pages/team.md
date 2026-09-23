---
title: "Team"
layout: gridlay
sitemap: false
permalink: /team/
---

## Team

**We are looking for new team members!**

## PI

<div class="section-card">
<div class="pi-card">
<img src="{{ site.url }}{{ site.baseurl }}/images/{{ site.photo }}" class="pi-photo" alt="{{ site.name }}" loading="lazy">
<div>
<h3 class="pi-name">{{ site.name }}</h3>
<p style="font-style: italic; color: var(--text-secondary); margin: 0;">{{ site.title }}</p>
{% if site.department %}<p style="color: var(--text-secondary); margin: 0;">{{ site.department }}</p>{% endif %}
{% if site.college %}<p style="color: var(--text-secondary); margin: 0;">{{ site.college }}</p>{% endif %}
<p style="color: var(--text-tertiary); font-size: 0.9rem; margin: 0;">{{ site.institution }}{% if site.institution_location %}, {{ site.institution_location }}{% endif %}</p>
<div class="pi-links">
{% if site.email %}<a href="mailto:{{ site.email }}" class="icon-link" title="Email"><i class="fa-solid fa-envelope"></i></a>{% endif %}
{% if site.links.cv and site.links.cv != "" %}<a href="{{ site.url }}{{ site.baseurl }}/{{ site.links.cv }}" class="icon-link" title="CV"><i class="ai ai-cv"></i></a>{% endif %}
{% if site.links.google_scholar and site.links.google_scholar != "" %}<a href="{{ site.links.google_scholar }}" class="icon-link" title="Google Scholar"><i class="ai ai-google-scholar"></i></a>{% endif %}
{% if site.links.github and site.links.github != "" %}<a href="{{ site.links.github }}" class="icon-link" title="GitHub"><i class="fa-brands fa-github"></i></a>{% endif %}
{% if site.links.researchgate and site.links.researchgate != "" %}<a href="{{ site.links.researchgate }}" class="icon-link" title="ResearchGate"><i class="ai ai-researchgate"></i></a>{% endif %}
{% if site.links.orcid and site.links.orcid != "" %}<a href="{{ site.links.orcid }}" class="icon-link" title="ORCID"><i class="ai ai-orcid"></i></a>{% endif %}
{% if site.links.twitter and site.links.twitter != "" %}<a href="{{ site.links.twitter }}" class="icon-link" title="Twitter"><i class="fa-brands fa-x-twitter"></i></a>{% endif %}
{% if site.links.linkedin and site.links.linkedin != "" %}<a href="{{ site.links.linkedin }}" class="icon-link" title="LinkedIn"><i class="fa-brands fa-linkedin"></i></a>{% endif %}
{% if site.links.youtube and site.links.youtube != "" %}<a href="{{ site.links.youtube }}" class="icon-link" title="YouTube"><i class="fa-brands fa-youtube"></i></a>{% endif %}
</div>
</div>
</div>
</div>

<!-- 1. 研究生 (M.E.) 循环区块 -->
{% assign me_students = site.data.web.people.students | where: "category", "M.E." | where_exp: "s", "s.show_team == true" %}
{% if me_students.size > 0 %}
## Graduate Students

<div class="team-grid">
{% for member in me_students %}
<div class="team-card">
<img src="{{ site.url }}{{ site.baseurl }}/images/{{ member.photo }}" class="team-photo" alt="{{ member.name }}" loading="lazy">
<h4 class="team-name">{{ member.name }}</h4>
<p class="team-info">{{ member.info }}</p>
{% if member.research_focus and member.research_focus != "" %}
<p class="team-info" style="font-size: 0.85rem; color: var(--text-secondary); margin-top: 4px;"><strong>Research:</strong> {{ member.research_focus }}</p>
{% endif %}
{% if member.lamar_id and member.lamar_id != "" %}<p class="team-info">{{ member.lamar_id }}</p>{% endif %}
<div class="team-links">
{% if member.email %}<a href="mailto:{{ member.email }}" class="icon-link" title="Email"><i class="fa-solid fa-envelope"></i></a>{% endif %}
{% if member.website %}<a href="{{ member.website }}" class="icon-link" title="Website"><i class="fa-solid fa-house"></i></a>{% endif %}
{% if member.scholar %}<a href="{{ member.scholar }}" class="icon-link" title="Google Scholar"><i class="ai ai-google-scholar"></i></a>{% endif %}
{% if member.github %}<a href="{{ member.github }}" class="icon-link" title="GitHub"><i class="fa-brands fa-github"></i></a>{% endif %}
</div>
</div>
{% endfor %}
</div>
{% endif %}

<!-- 2. 本科生循环区块（按 info 中的年份自动分行分组） -->
{% assign be_students = site.data.web.people.students | where_exp: "s", "s.category != 'M.E.' and s.show_team == true" %}
{% if be_students.size > 0 %}
## Undergraduate Students

{% assign years_str = "" %}
{% for member in be_students %}
  {% assign y = member.info | slice: 0, 4 %}
  {% if y != "" %}
    {% unless years_str contains y %}
      {% assign years_str = years_str | append: y | append: "," %}
    {% endunless %}
  {% endif %}
{% endfor %}
{% assign year_list = years_str | split: "," | sort %}

{% for year in year_list %}
{% if year != "" %}
<div class="team-grid" style="margin-bottom: 24px;">
{% for member in be_students %}
  {% assign member_year = member.info | slice: 0, 4 %}
  {% if member_year == year %}
  <div class="team-card">
  <img src="{{ site.url }}{{ site.baseurl }}/images/{{ member.photo }}" class="team-photo" alt="{{ member.name }}" loading="lazy">
  <h4 class="team-name">{{ member.name }}</h4>
  <p class="team-info">{{ member.info }}</p>

  {% if member.next_position and member.next_position != "" %}
  <p class="team-info">{{ member.next_position }}</p>
  {% endif %}

  {% if member.research_focus and member.research_focus != "" %}
  <p class="team-info" style="font-size: 0.85rem; color: var(--text-secondary); margin-top: 4px;"><strong>Research:</strong> {{ member.research_focus }}</p>
  {% endif %}
  {% if member.lamar_id and member.lamar_id != "" %}<p class="team-info">{{ member.lamar_id }}</p>{% endif %}
  <div class="team-links">
  {% if member.email %}<a href="mailto:{{ member.email }}" class="icon-link" title="Email"><i class="fa-solid fa-envelope"></i></a>{% endif %}
  {% if member.website %}<a href="{{ member.website }}" class="icon-link" title="Website"><i class="fa-solid fa-house"></i></a>{% endif %}
  {% if member.scholar %}<a href="{{ member.scholar }}" class="icon-link" title="Google Scholar"><i class="ai ai-google-scholar"></i></a>{% endif %}
  {% if member.github %}<a href="{{ member.github }}" class="icon-link" title="GitHub"><i class="fa-brands fa-github"></i></a>{% endif %}
  </div>
  </div>
  {% endif %}
{% endfor %}
</div>
{% endif %}
{% endfor %}
{% endif %}

<!-- 3. 校友 (Alumni) 卡片区块 -->
{% if site.data.web.people.alumni.size > 0 %}
## Alumni

<div class="team-grid">
{% assign sorted_alumni = site.data.web.people.alumni | sort: "year_end" | reverse %}
{% for member in sorted_alumni %}
<div class="team-card">
{% if member.photo and member.photo != "" %}
<img src="{{ site.url }}{{ site.baseurl }}/images/{{ member.photo }}" class="team-photo" alt="{{ member.name }}" loading="lazy">
{% else %}
<img src="{{ site.url }}{{ site.baseurl }}/images/teampic/default_avatar.jpg" class="team-photo" alt="{{ member.name }}" loading="lazy">
{% endif %}
<h4 class="team-name">{{ member.name }}</h4>
<p class="team-info">{{ member.degree }}{% if member.year_start %} ({{ member.year_start }}{% if member.year_end %} – {{ member.year_end }}{% endif %}){% endif %}</p>

{% if member.current_position and member.current_position != "" %}
<p class="team-info" style="font-size: 0.85rem; color: var(--text-secondary); margin-top: 4px;"><strong>Current:</strong> {{ member.current_position }}</p>
{% endif %}

{% if member.research_focus and member.research_focus != "" %}
<p class="team-info" style="font-size: 0.85rem; color: var(--text-secondary); margin-top: 4px;"><strong>Research:</strong> {{ member.research_focus }}</p>
{% endif %}

{% if member.thesis and member.thesis != "" %}
<p class="team-info" style="font-size: 0.85rem; color: var(--text-secondary); margin-top: 4px; font-style: italic;"><strong>Thesis:</strong> {{ member.thesis }}</p>
{% endif %}

<div class="team-links">
{% if member.email %}<a href="mailto:{{ member.email }}" class="icon-link" title="Email"><i class="fa-solid fa-envelope"></i></a>{% endif %}
{% if member.website %}<a href="{{ member.website }}" class="icon-link" title="Website"><i class="fa-solid fa-house"></i></a>{% endif %}
{% if member.scholar %}<a href="{{ member.scholar }}" class="icon-link" title="Google Scholar"><i class="ai ai-google-scholar"></i></a>{% endif %}
{% if member.github %}<a href="{{ member.github }}" class="icon-link" title="GitHub"><i class="fa-brands fa-github"></i></a>{% endif %}
</div>
</div>
{% endfor %}
</div>
{% endif %}

{% assign collab_list = site.data.web.people.collaborators | where_exp: "c", "c.show_collaborator == true" | sort: "last_name" %}
{% if collab_list.size > 0 %}
## Collaborators

<div class="section-card">
<table class="alumni-table">
<thead>
<tr><th>Name</th><th>Affiliation</th></tr>
</thead>
<tbody>
{% for c in collab_list %}
<tr>
<td data-label="Name">{% if c.website and c.website != "" %}<a href="{{ c.website }}" target="_blank">{{ c.name }}</a>{% else %}{{ c.name }}{% endif %}</td>
<td data-label="Affiliation">{% if c.email and c.email != "" %}<a href="mailto:{{ c.email }}">{{ c.affiliation }}</a>{% else %}{{ c.affiliation }}{% endif %}</td>
</tr>
{% endfor %}
</tbody>
</table>
</div>
{% endif %}

{% if site.data.web.people.other and site.data.web.people.other.size > 0 %}
## Administrative Support

<div class="section-card">
<ul>
{% for item in site.data.web.people.other %}
<li>{% if item.email %}<a href="mailto:{{ item.email }}">{{ item.name }}</a>{% else %}{{ item.name }}{% endif %}{% if item.role %} ({{ item.role }}){% endif %}</li>
{% endfor %}
</ul>
</div>
{% endif %}