---
permalink: /
title: "About Me"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

My name is Sam and I am a Computer Science student with the University of Louisville! In my work I have utilized data science for many different applications, and I am excited to continue applying it in my career!

<div class="slider">
  <div class="slider__slide">
    <img src="/images/IMG_4462.jpg" alt="Photo 1" />
  </div>
  <div class="slider__slide">
    <img src="/images/IMG_4862.JPG" alt="Photo 2" />
  </div>
  <div class="slider__slide">
    <img src="/images/IMG_2055.jpg" alt="Photo 3" />
  </div>
  <div class="slider__slide">
    <img src="/images/IMG_3491.jpg" alt="Photo 4" />
  </div>
  <div class="slider__slide">
    <img src="/images/IMG_4756.jpg" alt="Photo 5" />
  </div>
  <div class="slider__slide">
    <img src="/images/IMG_4860.JPG" alt="Photo 6" />
  </div>
  <div class="slider__slide">
    <img src="/images/IMG_6134.jpg" alt="Photo 7" />
  </div>
  <div class="slider__slide">
    <img src="/images/capstonephoto.jpg" alt="Capstone Team Photo" />
  </div>
</div>

<style>
.slider {
  --slider-width: 640px;
  --slider-height: 320px;
  --slider-border-width: 4px;
  --slider-frame-color: #ffffff;

  position: relative;
  width: var(--slider-width);
  height: var(--slider-height);
  margin: 20px auto;
  overflow: hidden;
  border: var(--slider-border-width) solid var(--slider-frame-color);
  border-radius: 4px;
  transition: border-color 0s ease-in-out;
}

html[data-theme="dark"] .slider {
  --slider-frame-color: #383a3d;
}

html:not([data-theme="dark"]) .slider {
  --slider-frame-color: #d1d1d1;
}

.slider__slide {
  position: absolute;
  inset: 0;
  opacity: 0;
  transition: opacity 0.8s ease-in-out;
}

.slider__slide img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.slider__slide img[src="/images/IMG_2055.jpg"] {
  object-position: center calc(50% + 15px);
}

.slider__slide img[src="/images/IMG_4860.JPG"] {
  object-position: center calc(50% + 50px);
}

.slider__slide img[src="/images/IMG_6134.jpg"] {
  object-position: center calc(50% + 200px);
}

.slider__slide img[src="/images/capstonephoto.jpg"] {
  object-position: center 20%;
}

.slider__slide.is-active {
  opacity: 1;
}

</style>

<script>
  (function () {
    var slides = document.querySelectorAll('.slider .slider__slide');
    if (!slides.length) return;

    var current = 0;
    slides[current].classList.add('is-active');

    setInterval(function () {
      slides[current].classList.remove('is-active');
      current = (current + 1) % slides.length;
      slides[current].classList.add('is-active');
    }, 2000);
  })();
</script>

<div style="text-align: center; margin-top: 24px;">
  <p>Interested in my background and experience?</p>
  <a href="/cv/" class="btn btn--primary">View My CV</a>
</div>