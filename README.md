<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <title>Мой браузер</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Segoe UI', sans-serif;
      background: linear-gradient(to right, #121212, #1e1e1e);
      color: #fff;
      height: 100vh;
      display: flex;
      flex-direction: column;
    }

    header {
      background-color: #222;
      padding: 10px 20px;
      display: flex;
      align-items: center;
      gap: 10px;
    }

    input[type="text"] {
      flex: 1;
      padding: 8px;
      font-size: 16px;
      border: none;
      border-radius: 4px;
    }

    button {
      padding: 8px 16px;
      font-size: 16px;
      border: none;
      background-color: #4CAF50;
      color: white;
      border-radius: 4px;
      cursor: pointer;
      transition: background 0.3s ease;
    }

    button:hover {
      background-color: #45a049;
    }

    .tabs {
      display: flex;
      background: #111;
      padding: 10px 20px;
      gap: 15px;
    }

    .tab {
      cursor: pointer;
      padding: 8px 12px;
      background: #333;
      border-radius: 6px;
      transition: 0.3s;
    }

    .tab:hover {
      background: #555;
    }

    .active-tab {
      background: #4CAF50;
    }

    iframe {
      flex-grow: 1;
      width: 100%;
      border: none;
    }

    .welcome {
      padding: 30px;
      text-align: center;
      background: radial-gradient(circle, #333, #111);
    }

    .gallery {
      display: flex;
      justify-content: center;
      gap: 30px;
      padding: 30px;
      flex-wrap: wrap;
    }

    .card {
      background: #1a1a1a;
      border-radius: 12px;
      overflow: hidden;
      width: 300px;
      box-shadow: 0 10px 25px rgba(0, 0, 0, 0.5);
      transition: transform 0.3s;
    }

    .card:hover {
      transform: translateY(-10px);
    }

    .card img {
      width: 100%;
      height: 200px;
      object-fit: cover;
    }

    .card p {
      padding: 15px;
      color: #ccc;
    }
  </style>
</head>
<body>

  <header>
    <input type="text" id="urlInput" placeholder="Введите сайт, например: wikipedia.org">
    <button onclick="goToUrl()">Перейти</button>
  </header>

  <div class="tabs">
    <div class="tab active-tab" onclick="loadTab('home')">🏠 Главная</div>
    <div class="tab" onclick="loadTab('https://instagram.com')">🌐 Сайт 1</div>
    <div class="tab" onclick="loadTab('https://gmail.com')">🔎 Сайт 2</div>
    <div class="tab" onclick="loadTab('https://wikipedia.org')">📚 Сайт 3</div>
    <div class="tab" onclick="loadTab('https://www.youtube.com/)">📚 Сайт 4</div>
  </div>

  <div id="content" style="flex-grow: 1; overflow: auto;">
    <div class="welcome">
      <h1>Добро пожаловать в мой браузер</h1>
      <p>Здесь вы можете посещать сайты и наслаждаться красивым интерфейсом!</p>
    </div>

    <div class="gallery">
      <div class="card">
        <img src="https://images.unsplash.com/photo-1537498425277-c283d32ef9db" alt="City">
        <p>Современный стиль 3D города.</p>
      </div>
      <div class="card">
        <img src="https://images.unsplash.com/photo-1581093588401-1b99f9a7b144" alt="Sky">
        <p>Природа и закат в объёмной перспективе.</p>
      </div>
      <div class="card">
        <img src="https://images.unsplash.com/photo-1618221199486-a40c3d59c2f8" alt="Code">
        <p>Веб-разработка и кодинг в стиле 3D.</p>
      </div>
    </div>
  </div>

  <iframe id="browserFrame" style="display: none;"></iframe>

  <script>
    function goToUrl() {
      let input = document.getElementById("urlInput").value.trim();
      if (!input.startsWith("http://") && !input.startsWith("https://")) {
        input = "https://" + input;
      }
      loadTab(input);
    }

    function loadTab(src) {
      const tabs = document.querySelectorAll('.tab');
      tabs.forEach(t => t.classList.remove('active-tab'));
      
      if (src === 'home') {
        document.getElementById("content").style.display = "block";
        document.getElementById("browserFrame").style.display = "none";
        tabs[0].classList.add('active-tab');
      } else {
        document.getElementById("browserFrame").src = src;
        document.getElementById("browserFrame").style.display = "block";
        document.getElementById("content").style.display = "none";
<header>
  <input type="text" id="urlInput" placeholder="Введите сайт, например: wikipedia.org">
  <button onclick="goToUrl()">Перейти</button>
  <button onclick="toggleTheme()">🌗 Тема</button>
</header>
        tabs.forEach(tab => {
          if (tab.innerText.includes(src) || tab.innerText.includes("Сайт")) {
            tab.classList.add('active-tab');
          }
        });
      }
    }
  </script>

</body>
</html>
