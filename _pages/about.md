---
layout: about
title: about
permalink: /
math: true
profile:
  align: right
  image: ayanami-rei-pixiv-88718073.png
  image_circular: false
  more_info: |
    <div class="portrait-caption"><a href="https://www.pixiv.net/artworks/88718073" aria-label="View original artwork by DALIYANG on Pixiv">Art by DALIYANG ↗</a></div>
    <div class="personal-motto">
      <blockquote>I believe in <a href="https://en.wikipedia.org/wiki/Action_principles">the principle<br>of least action</a>.</blockquote>
      <div class="motto-equation">\(\delta S = 0\)</div>
    </div>
selected_papers: false
social: false
announcements:
  enabled: false
latest_posts:
  enabled: false
---

<div class="about-intro" markdown="1">

I am Liu Hanqing (刘汉青), a master's student in the [Koyama Lab](https://lab.koyama.xyz/en/) at [the University of Tokyo](https://www.u-tokyo.ac.jp/en/). Previously, I received a bachelor's degree in [physics](https://www.phys.tsinghua.edu.cn/phyen/) and a master's degree in [history](https://naturalknowledge.net/) from [Tsinghua University](https://www.tsinghua.edu.cn/en/).

I study the **theoretical foundations of deep learning**, with a particular interest in how simple learning rules give rise to complex, sometimes surprising behavior.

I am currently studying the properties of **deep generative models**, focusing on **generalization and memorization in diffusion models**. Previously, I investigated loss spikes during neural network training and provided [an explanation for the Slingshot mechanism](https://arxiv.org/abs/2605.06152).

My interests span **learning dynamics and generalization**, **generative models**, and **statistical physics**. I like connecting mathematical ideas with what actually happens when we train neural networks. See details on my [research page]({{ '/research/' | relative_url }}).

About my name: **Liu** is my surname, and **Hanqing** is my given name. I prefer the Chinese name order, **Liu Hanqing** (roughly pronounced "Lyoh Hahn-ching"). However, I consistently publish as **Hanqing Liu** to avoid duplicate Google Scholar entries (a lesson I've already learned the hard way).

In my free time, I enjoy traveling, cycling, reading, live shows, anime, and video games.

**I plan to apply for Fall 2028 PhD programs and welcome research collaborations** — please feel free to [reach out](mailto:{{ site.data.socials.email }}).

<div class="about-links">
  <div class="about-socials" role="group" aria-label="Social links">{% social_links %}</div>
</div>

</div>

<section class="home-section home-news" aria-labelledby="news-heading">
  <h2 id="news-heading">News</h2>
  <div class="news-list">
    {% assign announcements = site.news | sort: 'date' | reverse %}
    {% for item in announcements %}
    <div class="news-item">
      <time class="news-date" datetime="{{ item.date | date: '%Y-%m' }}">{{ item.date | date: '%Y.%m' }}</time>
      <div class="news-body">{{ item.content | markdownify }}</div>
    </div>
    {% endfor %}
  </div>
</section>

<section class="home-section selected-papers" aria-labelledby="papers-heading">
  <h2 id="papers-heading"><a href="{{ '/publications/' | relative_url }}">Selected publications</a></h2>
  {% include selected_papers.liquid %}
</section>
