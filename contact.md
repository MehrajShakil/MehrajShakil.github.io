---
layout: page
title: Contact
subtitle: Let's connect — I'm always open to interesting conversations.
permalink: /contact/
---

<p>The best way to reach me is via email or any of the links below.</p>

<div class="contact-grid">
  {% if site.email != "" %}
  <a class="contact-card" href="mailto:{{ site.email }}">
    <p class="label">Email</p>
    <p class="value">{{ site.email }}</p>
  </a>
  {% endif %}
  {% if site.github_username != "" %}
  <a class="contact-card" href="https://github.com/{{ site.github_username }}" target="_blank" rel="noopener">
    <p class="label">GitHub</p>
    <p class="value">@{{ site.github_username }}</p>
  </a>
  {% endif %}
  {% if site.linkedin_username != "" %}
  <a class="contact-card" href="https://www.linkedin.com/in/{{ site.linkedin_username }}" target="_blank" rel="noopener">
    <p class="label">LinkedIn</p>
    <p class="value">/{{ site.linkedin_username }}</p>
  </a>
  {% endif %}
  {% if site.twitter_username != "" %}
  <a class="contact-card" href="https://twitter.com/{{ site.twitter_username }}" target="_blank" rel="noopener">
    <p class="label">Twitter</p>
    <p class="value">@{{ site.twitter_username }}</p>
  </a>
  {% endif %}
</div>
