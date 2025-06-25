---
layout: post
author: "jdcarvalho"
title: "Working with GitHub Pages is quite simple"
date: 2025-06-25 14:07:00
categories: [GitHub, Pages, Simple]
---

# Working with GitHub Pages is quite simple

## See the slider below
### See the slider below

<div class="swiper" style="width: 100%; max-width: 800px;">
  <div class="swiper-wrapper">
    <div class="swiper-slide"><img src="/assets/img/gallery/mountains/1.jpg" /></div>
    <div class="swiper-slide"><img src="/assets/img/gallery/mountains/2.jpg" /></div>
    <div class="swiper-slide"><img src="/assets/img/gallery/mountains/3.jpg" /></div>
  </div>
  <!-- Botões -->
  <div class="swiper-button-next"></div>
  <div class="swiper-button-prev"></div>
</div>

<script>
  new Swiper('.swiper', {
    loop: true,
    navigation: {
      nextEl: '.swiper-button-next',
      prevEl: '.swiper-button-prev',
    },
    autoplay: {
      delay: 3000,
    },
  });
</script>

