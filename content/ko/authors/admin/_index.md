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
    label: E-mail Me
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

<!-- 슬라이더 추가 -->
<div class="slider">
  <div class="slides">
    <div class="slide">
      <img src="/images/slide1.jpg" alt="슬라이드 1">
    </div>
    <div class="slide">
      <img src="/images/slide2.jpg" alt="슬라이드 2">
    </div>
    <div class="slide">
      <img src="/images/slide3.jpg" alt="슬라이드 3">
    </div>
  </div>
</div>

<style>
  .slider {
    position: relative;
    width: 100%;
    max-width: 600px;
    margin: auto;
    overflow: hidden;
  }
  .slides {
    display: flex;
    transition: transform 0.5s ease-in-out;
  }
  .slide {
    min-width: 100%;
    box-sizing: border-box;
  }
  .slide img {
    width: 100%;
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