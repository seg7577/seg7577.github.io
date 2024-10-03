---
title: m._.se0k
name_pronunciation: Kwon Min Seok
first_name: Min Seok
last_name: Kwon
status:
  icon: ☕️
superuser: true
role: Student
organizations:
  - name: 📍Jeonbuk National University Department of Computer Engineering
    url: https://www.jbnu.ac.kr
bio: "I am a full-stack developer in training."
profiles:
  - icon: at-symbol
    url: 'mailto:seg082911@gmail.com'
    label: E-mail Me
  - icon: brands/youtube
    url: https://youtu.be/wrmyqKRGW-0?si=L_rm299OkAZ_bbMm
  - icon: brands/instagram
    url: https://www.instagram.com/m._.se0k/
  - icon: brands/github
    url: https://www.github.com/
  - icon: phone
    url: 'tel:+821087704710'
  - icon: academicons/cv
    url: uploads/resume.pdf
    label: Download my resume
highlight_name: true
website: ""
---

<div style="background-color: #fff9c4; border-left: 5px solid #ffeb3b; padding: 20px; margin: 20px 0; border-radius: 3px; box-shadow: 2px 2px 8px rgba(0, 0, 0, 0.1); font-family: 'Inter', sans-serif, monospace; color: #333; font-size: 14px; line-height: 1.4">
  📍 Hello
  I am Minseok Kwon, a student majoring in Computer Engineering at Jeonbuk National University.
  I am primarily interested in full-stack development and cloud computing, and I am studying the latest web technologies and cloud architectures. I am gaining experience in both backend and frontend development in order to become a full-stack developer. Through team projects and personal endeavors, I aim to solve practical problems and am always open to new challenges. On my website, I share various articles related to development, as well as my hobbies and personal interests. 
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
  }, 3000);
</script>
