---
title: 나!   #문서의 제목
hide_date: true     #문서를 화면에 표시할 때 날짜를 숨기도록 지정
reading_time: false #읽기 시간을 표시하지 않겠다는 뜻 content 하위는 그냥 싹 다 body
---
## 반갑습니다.😀
전북대학교 컴퓨터공학부 2학년에 재학 중인 권민석이라고 합니다. 주로 풀스택 개발과 클라우드 개발에 관심을 가지고 있으며, 최신 웹 기술과 클라우드 아키텍처에 대해 공부하고 있습니다. 풀스택 개발자가 되기 위해 백엔드, 프론트엔드에 대한 경험을 쌓고 있습니다. 팀 프로젝트나 개인 프로젝트를 통해 실용적인 문제 해결을 목표로 하고 있으며, 새로운 도전에 항상 열려 있습니다. 저의 사이트는 이러한 경험을 바탕으로 개발에 관련된 다양한 글들과 저의 취미생활 등을 공유하고 있습니다.

## Contact
- 전화 : (+82)10-8770-4710
- 메일 : seg082911@gmail.com
- 주소 : 전북대학교 공과대학 7호관, 대한민국 전라북도 전주시 덕진구 백제대로 567
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