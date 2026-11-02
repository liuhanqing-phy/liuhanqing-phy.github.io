---
layout: page
permalink: /research/
title: Research
nav: true
nav_title: research
nav_order: 1
---

{% for interest in site.data.research %}
<section class="research-detail" aria-labelledby="{{ interest.id }}">
  <h2 id="{{ interest.id }}">{{ interest.title }}</h2>
  {{ interest.body | markdownify }}
</section>
{% endfor %}

[Read selected publications →]({{ '/publications/' | relative_url }})
