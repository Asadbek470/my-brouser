

<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Браузер "Реки"</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@700&display=swap');

        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
            background-color: #121212;
            color: #e0e0e0;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            text-align: center;
            overflow: hidden;
            position: relative;
        }

        body::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: url('https://images.unsplash.com/photo-1519681393784-d120267933ba?q=80&w=1740&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D');
            background-size: cover;
            background-position: center;
            filter: brightness(0.6) blur(3px);
            z-index: -1;
            animation: background-zoom 20s infinite alternate;
        }

        @keyframes background-zoom {
            0% { transform: scale(1); }
            100% { transform: scale(1.1); }
        }

        .container {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 20px;
            background: rgba(0, 0, 0, 0.4);
            padding: 40px;
            border-radius: 20px;
            backdrop-filter: blur(10px);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.7);
            transform: perspective(1000px) rotateX(10deg);
            transition: transform 0.5s cubic-bezier(0.68, -0.55, 0.27, 1.55);
        }

        .container:hover {
            transform: perspective(1000px) rotateX(0deg);
        }

        h1 {
            font-family: 'Poppins', sans-serif;
            font-size: 3em;
            color: #ffffff;
            text-shadow: 0 0 15px #00aaff, 0 0 25px #00aaff;
            letter-spacing: 5px;
            margin-bottom: 20px;
            transform-style: preserve-3d;
            animation: text-pop 2s cubic-bezier(0.68, -0.55, 0.27, 1.55) infinite;
        }

        @keyframes text-pop {
            0% { transform: translateZ(0); }
            50% { transform: translateZ(20px); }
            100% { transform: translateZ(0); }
        }

        .search-bar {
            width: 500px;
            max-width: 90%;
            display: flex;
            border-radius: 25px;
            overflow: hidden;
            background-color: rgba(44, 44, 44, 0.8);
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.5);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .search-bar input {
            flex-grow: 1;
            border: none;
            outline: none;
            padding: 15px 20px;
            font-size: 16px;
            background-color: transparent;
            color: #e0e0e0;
        }

        .search-bar button {
            border: none;
            background-color: #0077b6;
            color: #e0e0e0;
            padding: 0 20px;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .search-bar button:hover {
            background-color: #00b4d8;
        }

        .links {
            display: flex;
            gap: 20px;
            margin-top: 20px;
        }

        .link-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            text-decoration: none;
            color: inherit;
            transition: transform 0.2s, box-shadow 0.2s;
            position: relative;
        }

        .link-item:hover {
            transform: scale(1.1) translateY(-5px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.5);
        }

        .link-item img {
            width: 60px;
            height: 60px;
            border-radius: 15px;
            object-fit: cover;
            border: 2px solid #00aaff;
            box-shadow: 0 0 15px rgba(0, 170, 255, 0.5);
        }

        .link-item span {
            margin-top: 8px;
            font-size: 14px;
            color: #a0a0a0;
            text-shadow: 1px 1px 2px #000;
        }
    </style>
</head>
<body>

    <div class="container">
        <h1>Браузер "Реки"</h1>
        <div class="search-bar">
            <input type="text" id="searchInput" placeholder="Поиск в Google, YouTube или Telegram...">
            <button onclick="performSearch()">Искать</button>
        </div>

        <div class="links">
            <a href="https://www.google.com" class="link-item">
                <img src="https://www.google.com/s2/favicons?domain=google.com" alt="Google">
                <span>Google</span>
            </a>
            <a href="https://www.youtube.com" class="link-item">
                <img src="https://www.google.com/s2/favicons?domain=youtube.com" alt="YouTube">
                <span>YouTube</span>
            </a>
            <a href="https://www.instagram.com" class="link-item">
                <img src="https://www.google.com/s2/favicons?domain=instagram.com" alt="Instagram">
                <span>Instagram</span>
            </a>
            <a href="https://web.telegram.org" class="link-item">
                <img src="https://www.google.com/s2/favicons?domain=telegram.org" alt="Telegram">
                <span>Telegram</span>
            </a>
        </div>
    </div>

    <script>
        function performSearch() {
            const query = document.getElementById('searchInput').value;
            if (query) {
                // Если пользователь ищет на YouTube или Telegram, перенаправляем туда
                if (query.toLowerCase().includes('youtube')) {
                    window.location.href = `https://www.youtube.com/results?search_query=${encodeURIComponent(query)}`;
                } else if (query.toLowerCase().includes('telegram')) {
                    window.location.href = `https://web.telegram.org/a/#?q=${encodeURIComponent(query)}`;
                } else {
                    // В остальных случаях ищем в Google
                    window.location.href = `https://www.google.com/search?q=${encodeURIComponent(query)}`;
                }
            }
        }

        document.getElementById('searchInput').addEventListener('keypress', function(event) {
            if (event.key === 'Enter') {
                performSearch();
            }
        });
    </script>

</body>
</html>
