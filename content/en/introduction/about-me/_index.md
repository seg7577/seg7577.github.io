---
title: About-me    #문서의 제목
date: 2024-09-14    #문서가 생성되거나 발행된 날짜를 의미함
hide_date: true     #문서를 화면에 표시할 때 날짜를 숨기도록 지정
reading_time: false #읽기 시간을 표시하지 않겠다는 뜻 content 하위는 그냥 싹 다 body

---

## Hi😀
I am Minseok Kwon, a student majoring in Computer Engineering at Jeonbuk National University. I am primarily interested in full-stack development and cloud computing, and I am studying the latest web technologies and cloud architectures. I am gaining experience in both backend and frontend development in order to become a full-stack developer. Through team projects and personal endeavors, I aim to solve practical problems and am always open to new challenges. On my website, I share various articles related to development, as well as my hobbies and personal interests. 

## Contact
- phone : (+82)10-8770-4710
- mail : seg082911@gmail.com
- address : Jeonbuk National University, College of Engineering, Building 7, 567 Baekje-daero, Deokjin-gu, Jeonju-si, Jeollabuk-do, 54896, Republic of Korea
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