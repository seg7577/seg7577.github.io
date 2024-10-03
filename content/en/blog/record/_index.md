---
title: "Record"
description: "This is an image gallery page"
---

# Welcome to the Image Gallery

Here are some beautiful images displayed in a responsive gallery:
<style>
  .gallery {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    grid-gap: 15px;
    padding: 20px;
    max-width: 1200px;
    margin: 0 auto;
  }

  .gallery-item {
    overflow: hidden;
  }

  .gallery-item img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.3s ease;
  }

  .gallery-item:hover img {
    transform: scale(1.1);
  }
</style>
<div class="gallery">
  <div class="gallery-item">
    <img src="/images/gallery/image1.jpg" alt="Image 1">
  </div>
  <div class="gallery-item">
    <img src="/images/gallery/image2.jpg" alt="Image 2">
  </div>
  <div class="gallery-item">
    <img src="/images/gallery/image3.jpg" alt="Image 3">
  </div>
  <div class="gallery-item">
    <img src="/images/gallery/image4.jpg" alt="Image 4">
  </div>
  <div class="gallery-item">
    <img src="/images/gallery/image5.jpg" alt="Image 5">
  </div>
  <div class="gallery-item">
    <img src="/images/gallery/image6.jpg" alt="Image 6">
  </div>
</div>

You can hover over the images to see a zoom effect!
