---
# Display name
title: m._.se0k

# Name pronunciation (optional)
name_pronunciation: 권민석
# Full name (for SEO)
first_name: 민석
last_name: 권

# Status emoji
status:
  icon: ☕️

# Is this the primary user of the site?
superuser: true

# Role/position/tagline
role: 학생

organizations:
  - name: 전북대학교 컴퓨터 공학부
    url: https://www.jbnu.ac.kr

# Short bio (displayed in user profile at end of posts)
bio: 저는 전북대학교에서 컴퓨터공학을 전공하고 있는 학생 권민석입니다.
# Social Networking
# Need to use another icon? Simply download the SVG icon to your `assets/media/icons/` folder.
profiles:
  - icon: at-symbol
    url: 'mailto:seg082911@gmail.com'
  - icon: brands/youtube
    url: https://youtu.be/wrmyqKRGW-0?si=L_rm299OkAZ_bbMm
  - icon: brands/instagram
    url: https://www.instagram.com/m._.se0k/
  - icon: brands/github
    url: https://github.com/seg7577
  - icon: phone
    url: 'tel:+821087704710'
  # Link to a PDF of your resume/CV - upload it to `static/uploads/resume.pdf`
  - icon: academicons/cv
    url: uploads/resume.pdf
# Highlight the author in author lists? (true/false)
highlight_name: true

# Author's website URL
website: ""
---

<div style="background-color: #fff9c4; border-left: 5px solid #ffeb3b; padding: 20px; margin: 20px 0; border-radius: 3px; box-shadow: 2px 2px 8px rgba(0, 0, 0, 0.1); font-family: 'Courier New', Courier, monospace; color: #333; font-size: 14px; line-height: 1.4">
  📍 안녕하세요. 저는 전북대학교에서 컴퓨터공학을 전공하고 있는 학생 권민석입니다.
  주로 풀스택 개발과 클라우드 개발에 관심을 가지고 있으며, 최신 웹 기술과 클라우드 아키텍처에 대해 공부하고 있습니다. 풀스택 개발자가 되기 위해 백엔드, 프론트엔드에 대한 경험을 쌓고 있습니다. 팀 프로젝트나 개인 프로젝트를 통해 실용적인 문제 해결을 목표로 하고 있으며, 새로운 도전에 항상 열려 있습니다. 저의 사이트는 이러한 경험을 바탕으로 개발에 관련된 다양한 글들과 저의 취미생활 등을 공유하고 있습니다.
</div>

<!-- OpenStreetMap 지도 추가 -->
<div id="map" style="height: 400px; width: 100%;"></div>

<!-- Leaflet.js 라이브러리 추가 -->
<script src="https://unpkg.com/leaflet@1.7.1/dist/leaflet.js"></script>
<link rel="stylesheet" href="https://unpkg.com/leaflet@1.7.1/dist/leaflet.css" />

<!-- OpenStreetMap 지도 초기화 스크립트 -->
<script>
    var map = L.map('map').setView([35.84601324617979, 127.13444961966684], 13);  // 위도, 경도 및 줌 설정
    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
        attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
    }).addTo(map);

    var marker = L.marker([35.84601324617979, 127.13444961966684]).addTo(map)
        .bindPopup('전북대학교 공과대학 7호관 위치')
        .openPopup();
</script>
<!-- 이미지 슬라이더 추가 -->
<div class="slider">
  <div class="slides">
    <div class="slide">
      <img src="/images/slider/slide1.jpg" alt="슬라이드 1">
      <div class="overlay"></div>
      <div class="text-overlay">me</div>
    </div>
    <div class="slide">
      <img src="/images/slider/slide2.jpg" alt="슬라이드 2">
      <div class="overlay"></div>
      <div class="text-overlay">me</div>
    </div>
    <div class="slide">
      <img src="/images/slider/slide3.jpg" alt="슬라이드 3">
      <div class="overlay"></div>
      <div class="text-overlay">me</div>
    </div>
    <div class="slide">
      <img src="https://images.unsplash.com/photo-1593642532973-d31b6557fa68?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwzNjUyOXwwfDF8c2VhcmNofDJ8fHRlY2hub2xvZ3l8ZW58MHx8fHwxNjIzNTI1NzA4&ixlib=rb-1.2.1&q=80&w=1080" alt="슬라이드 4">
      <div class="overlay"></div>
      <div class="text-overlay">Unsplash의Kari Shea</div>
    </div>
    <div class="slide">
      <img src="https://images.unsplash.com/photo-1714291067290-10c5956a9fa0?q=80&w=1587&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" alt="슬라이드 5">
      <div class="overlay"></div>
      <div class="text-overlay">Unsplash의Ahmed</div>
    </div>
    <div class="slide">
      <img src="https://images.unsplash.com/photo-1727396561097-314b2baf1f9c?q=80&w=1480&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" alt="슬라이드 6">
      <div class="overlay"></div>
      <div class="text-overlay">Unsplash의BoranPang</div>
    </div>
  </div>
</div>

  
  
<style>
  /* 슬라이더 컨테이너 */
  .slider {
    position: relative;
    width: 100%;
    max-width: 600px;
    margin: auto;
    overflow: hidden;
  }

  /* 슬라이드들을 감싸는 컨테이너 */
  .slides {
    display: flex;
    transition: transform 0.5s ease-in-out;
  }

  /* 개별 슬라이드 */
  .slide {
    position: relative;
    min-width: 100%;
    box-sizing: border-box;
  }
  .slide img {
    width: 100%;
    display: block;
  }

  /* 이미지 위에 덮이는 반투명한 레이어 */
  .overlay {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
  }

  /* 텍스트 오버레이 */
  .text-overlay {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    color: white;
    font-size: 24px;
    text-align: center;
    z-index: 2;
  }
</style>

<script>
  let currentSlide = 0;
  const slides = document.querySelector('.slides');
  const totalSlides = document.querySelectorAll('.slide').length;

  setInterval(() => {
    currentSlide = (currentSlide + 1) % totalSlides;
    slides.style.transform = `translateX(-${currentSlide * 100}%)`;
  }, 1000);
</script>
