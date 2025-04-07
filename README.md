<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>서울 계절별 별자리</title>
  <script src="https://slowe.github.io/VirtualSky/script/virtualsky.min.js"></script>
  <style>
    body {
      text-align: center;
      font-size: 1.5rem;
      background-color: black;
      color: white;
      margin: 0;
      padding: 20px;
      font-family: Arial, sans-serif;
    }

    button {
      font-size: 1.2rem;
      margin: 10px;
      padding: 10px 20px;
      border: none;
      border-radius: 10px;
      background-color: #444;
      color: white;
      cursor: pointer;
    }

    button:hover {
      background-color: #666;
    }

    #starmap {
      width: 100%;
      height: 80vh;
      margin-top: 20px;
    }
  </style>
</head>
<body>
  <h1>서울 계절별 별자리</h1>
  <p>계절을 선택하면 해당 계절의 별자리를 볼 수 있어요!</p>
  
  <button onclick="showSeasonSky('spring')">봄</button>
  <button onclick="showSeasonSky('summer')">여름</button>
  <button onclick="showSeasonSky('autumn')">가을</button>
  <button onclick="showSeasonSky('winter')">겨울</button>

  <div id="starmap"></div>

  <script>
    function showSeasonSky(season) {
      let date;
      switch(season) {
        case 'spring':
          date = new Date('2025-03-21T21:00:00'); // 춘분
          break;
        case 'summer':
          date = new Date('2025-06-21T21:00:00'); // 하지
          break;
        case 'autumn':
          date = new Date('2025-09-23T21:00:00'); // 추분
          break;
        case 'winter':
          date = new Date('2025-12-21T21:00:00'); // 동지
          break;
      }

      // 기존 starmap 초기화
      document.getElementById("starmap").innerHTML = "";

      virtualsky({
        id: "starmap",
        latitude: 37.5665,
        longitude: 126.9780,
        projection: "stereo",
        showconstellations: true,
        showstarlabels: true,
        showplanets: true,
        gradient: true,
        cardinalpoints: true,
        constellations: true,
        live: false,
        date: date.toISOString()
      });
    }
  </script>
</body>
</html>
