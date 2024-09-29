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

<!-- 이미지 슬라이더 추가 -->
<div class="slider">
  <div class="slides">
    <div class="slide">
    <!-- 첫번째 슬라이드, 순서대로 이미지 경로, overlay, text-overlay 적용 시킴 -->
      <img src="/images/slide1.jpg" alt="슬라이드 1">
      <div class="overlay"></div>
      <div class="text-overlay">text-overlay~!</div>
    </div>
    <div class="slide">
      <img src="/images/slide2.jpg" alt="슬라이드 2">
      <div class="overlay"></div>
      <div class="text-overlay">text-overlay2~!</div>
    </div>
    <div class="slide">
      <img src="/images/slide3.jpg" alt="슬라이드 3">
      <div class="overlay"></div>
      <div class="text-overlay">text-overlay3~!</div>
    </div>
  </div>
</div>

<style>
  /* 슬라이더 컨테이너 */
  .slider {
    position: relative; /*  슬라이더 안에서 위치를 기준으로 정렬하기 위해 사용  */
    width: 100%;        /*  슬라이더가 화면의 전체 너비를 차지하도록 설정 */
    max-width: 600px;   /*  슬라이더으 ㅣ최대 너비를 600px로 제한 -> 사진 수정시 유용할듯?  */
    margin: auto;       /*  중앙에 배치하기 위해 좌우 여백을 자동으로 설정  */
    overflow: hidden;   /*  슬라이더가 컨테이너 밖으로 넘어가지 않도록 설정 */
  }

  /* 슬라이드들을 감싸는 컨테이너 */
  .slides {
    display: flex;                              /*  슬라이드를 가로로 정렬하기 위해 flexbox 사용  */
    transition: transform 0.5s ease-in-out;     /*  슬라이드가 전환될 때 부드러운 애니메이션 적용 */
  }

  /* 개별 슬라이드 */
  .slide {
    position: relative;     /*  각 슬라이드를 기준으로 오버레이와 텍스트를 배치하기 위해 사용*/
    min-width: 100%;        /*  각 슬라이드가 슬라이더의 너비를 100% 차지하도록 설정  */
    box-sizing: border-box; /*  슬라이드 내의 여백과 패딩을 포함한 전체 크기를 설정 */
  }
  .slide img {
    width: 100%;
    display: block;
    /* 이미지를 슬라이드의 너비에 맞게 조정, 블록 요소로 처리하여 여백 문제를 해결 */
  }

  /* 이미지 위에 덮이는 반투명한 레이어 */
  .overlay {
    position: absolute; /*  슬라이드 내에서 절대 위치로 설정하여 이미지 위에 레이어를 덮음*/
    top: 0;   
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5); /* 검정색 반투명 */
  }

  /* 텍스트 오버레이 */
  .text-overlay {
    position: absolute; /*  슬라이드 내에서 절대 위치로 설정하여 텍스트를 배치  */
    top: 50%;           /*  슬라이드의 중앙에 배치  */
    left: 50%;          
    transform: translate(-50%, -50%); /*  중앙정렬을 위해 사용  */
    color: white;
    font-size: 24px;
    text-align: center;
    z-index: 2;         /* 텍스트가 오버레이 위에 나타나도록 설정 */
  }
</style>

<script>
  let currentSlide = 0; //현재 보여지는 슬라이드의 인덱스를 추정
  const slides = document.querySelector('.slides'); //슬라이드를 감싸는 컨테이너 선택
  const totalSlides = document.querySelectorAll('.slide').length; //전체 슬라이드

  // 일정 시간 간격으로 슬라이드를 전환하는 함수
  setInterval(() => {
    currentSlide = (currentSlide + 1) % totalSlides;  //다음 슬라이드로 이동, 마지막 슬라이드면 처음으로 돌아감
    slides.style.transform = `translateX(-${currentSlide * 100}%)`; //슬라이드를 왼쪽으로 이동시킴
  }, 3000); //3초마다 슬라이드 전환

</script>