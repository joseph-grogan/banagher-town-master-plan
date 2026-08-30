---
layout: default
title: Home
---

<section class="hero">
  <h1>Banagher Town Masterplan</h1>
  <p class="lead">Where History Meets Community, and Community Creates the Future</p>
  <p>
    The aim of this site is to show the community all the things that are happening
    — as well as things that could happen with the right support and expertise from the town.
    Please get involved where you can and lend a hand.
  </p>
</section>

<section class="featured">
  <h2>🚀 Featured: Banagher Meitheal</h2>
  <p>
    We're moving the <strong>Meitheal</strong> project forward — a modern take on the old Irish
    tradition of neighbours coming together. No committees, no meetings, no obligations.
    Just local people helping improve our town when they have a spare hour or two.
  </p>
  <p>
    <a href="{{ '/projects/meitheal/' | relative_url }}" class="btn">Read the full plan &rarr;</a>
  </p>
</section>

<section id="projects">
  <h2>Town Projects</h2>
  <div class="project-grid">
    {% for project in site.projects %}
    <a href="{{ project.url | relative_url }}" class="project-card">
      <span class="status-badge status-{{ project.status | slugify }}">{{ project.status }}</span>
      <h3>{{ project.title }}</h3>
      <p>{{ project.tagline }}</p>
    </a>
    {% endfor %}
  </div>
</section>
