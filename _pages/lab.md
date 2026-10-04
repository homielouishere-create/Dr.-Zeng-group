---
title: "Lab"
layout: gridlay
sitemap: false
permalink: /lab/
hero_image: images/lab/ketizu.jpg
---
## C-AIMS Lab

<div class="section-card">
<h3>About C-AIMS Lab</h3>
<p style="font-size: 0.95rem; line-height: 1.75; margin-bottom: var(--space-4);">
The <strong>Carbon & AI-driven Materials Simulation (C-AIMS) Laboratory</strong> is committed to pioneering next-generation energy storage solutions through the convergence of first-principles <strong>Density Functional Theory (DFT)</strong> calculations, Machine Learning, Topological Data Analysis (TDA), and Artificial Intelligence for Science (AI4S). 
Our primary research focuses on the atomic-scale design, electronic structure modeling, and electrochemical performance evaluation of novel <strong>two-dimensional (2D) carbon allotropes</strong> and nanostructures as high-performance anode materials for metal-ion batteries.
</p>
<p style="font-size: 0.95rem; line-height: 1.75; margin-bottom: var(--space-2);">
Our research focuses on four core directions:
</p>
<ul style="font-size: 0.95rem; line-height: 1.75; margin-bottom: var(--space-4); padding-left: 1.2rem;">
<li><strong>Molecular Design of 2D Battery Materials</strong>: Atomic-scale design, electronic structure modeling, and electrochemical performance evaluation of novel two-dimensional (2D) carbon allotropes and functional nanostructures as high-performance anode materials for metal-ion batteries.</li>
<li><strong>Excited-State Carrier Dynamics</strong>: Quantum simulation and ultrafast dynamical mechanisms of excited-state carriers in novel functional materials (including 2D materials and heterostructures).</li>
<li><strong>Novel Energy & Hydrogen Storage Materials</strong>: Theoretical prediction, fundamental physicochemical property characterization, and storage mechanism analysis of emerging clean energy materials.</li>
<li><strong>Structure Design of Smart Energetic Materials</strong>: Rational structural modeling, thermodynamic reactivity, and controlled initiation behaviors of (smart) controllable energetic materials.</li>
</ul>
</div>


{% include lab_news_carousel.html %}

## Research Focus

<div class="rf-grid" markdown="0">
{% for area in site.data.web.research_areas %}
<div class="section-card">
  <div class="rf-card">
    <div class="rf-image-wrap">
      <img src="{{ site.url }}{{ site.baseurl }}/images/{{ area.image }}" alt="{{ area.name }}" loading="lazy">
    </div>
    <div class="rf-content">
      <div class="rf-header">
        <span class="rf-number">{{ area.id }}</span>
        <h3 class="rf-name">{{ area.name }}</h3>
      </div>
      <p class="rf-desc">{{ area.description }}</p>
      <ul class="rf-projects">
        {% for proj in area.projects %}
        <li><a href="{{ site.url }}{{ site.baseurl }}/research/#{{ proj.slug }}">{{ proj.title }}</a></li>
        {% endfor %}
      </ul>
      <div class="rf-domains">
        {% for domain in area.domains %}
        <span class="chip chip-muted">{{ domain }}</span>
        {% endfor %}
      </div>
    </div>
  </div>
</div>
{% endfor %}
</div>

## Recent Research

{% assign _rr_video = nil %}
{% for v in site.data.videos %}{% if v.section == "research" and _rr_video == nil %}{% assign _rr_video = v %}{% endif %}{% endfor %}
{% if _rr_video %}

<div class="section-card rr-card" markdown="0">
<div class="rr-header">
<h3 class="rr-title">{{ _rr_video.title }}</h3>
</div>
<div class="rr-video-wrap">
<iframe src="{{ _rr_video.embed_src }}" title="{{ _rr_video.title }}" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>
<p class="rr-abstract">{{ _rr_video.abstract | strip_newlines | strip }}</p>
<div class="rr-actions">
<a href="{{ site.url }}{{ site.baseurl }}/videos/" class="rr-more-btn">Watch More »</a>
<a href="{{ site.url }}{{ site.baseurl }}/research/" class="rr-more-btn">Find More Projects »</a>
</div>
</div>
{% endif %}

## Equipment

<div class="equipment-grid">
{% for item in site.data.web.equipment %}
<div class="equipment-card">
{% if item.image and item.image != "" %}
<img src="{{ site.url }}{{ site.baseurl }}/images/{{ item.image }}" class="equipment-thumb" alt="{{ item.name }}" loading="lazy">
{% else %}
<div class="equipment-thumb-placeholder"><i class="fa-solid fa-microchip"></i></div>
{% endif %}
<div class="equipment-body">
<p class="equipment-category">{{ item.category }}</p>
<h4 class="equipment-name">{{ item.name }}</h4>
<p class="equipment-desc">{{ item.description }}</p>
</div>
</div>
{% endfor %}
</div>