---
layout: post
title: When the arithmetic becomes the dynamics
date: 2026-11-01 11:00:00 +0900
permalink: /blog/numerical-dynamics/
description: Finite precision is part of the learning system.
related_posts: false
---

<p class="draft-note">Preview note.</p>

A training algorithm is implemented in finite precision. Small numerical effects can change the dynamics we observe, so the behavior of a real computation can differ from its idealized equations.

This question motivates our work on Slingshot loss spikes. We study how finite-precision errors can disrupt gradient balance and drive rapid parameter growth during long-term training.

[Read the paper on arXiv](https://arxiv.org/abs/2605.06152) · [Back to the blog]({{ '/blog/' | relative_url }})
