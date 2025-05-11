<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mi Mundo - Anth'Zz Berrocal</title>
    <style>
        body {
            background: linear-gradient(135deg, #121212, #1f1f1f, #292929);
            color: #00ff88;
            font-family: 'Courier New', Courier, monospace;
            overflow: hidden;
            margin: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            touch-action: none;
        }
        h1 {
            font-size: 3em;
            margin-top: 20px;
            color: #00b3ff;
            text-shadow: 0 0 20px #00b3ff, 0 0 40px #00b3ff;
            font-family: 'Pacifico', sans-serif;
        }
        .game-container {
            position: relative;
            width: 100vw;
            height: 80vh;
            overflow: hidden;
            border: 5px solid #00b3ff;
            border-radius: 30px;
            margin: 20px 0;
            box-shadow: 0 0 50px #00b3ff;
        }
        .catcher {
            position: absolute;
            bottom: 20px;
            width: 150px;
            height: 50px;
            background-color: #00b3ff;
            border-radius: 25px;
            filter: drop-shadow(0 0 15px #00b3ff);
            border: 2px solid #fff;
            box-shadow: 0 0 20px #00b3ff;
        }
        .falling-photo {
            position: absolute;
            width: 120px;
            height: 120px;
            border-radius: 15px;
            border: 3px solid #fff;
            filter: drop-shadow(0 0 15px #00b3ff);
            animation: fall 6s linear infinite;
        }
        @keyframes fall {
            0% { top: -100px; }
            100% { top: 90vh; }
        }
        .score-container {
            font-size: 2.5em;
            color: #00ffcc;
            text-shadow: 0 0 15px #00ffcc, 0 0 30px #00ffcc;
            margin-bottom: 10px;
            display: flex;
            align-items: center;
        }
        .score-label {
            margin-right: 10px;
            color: #00b3ff;
            font-size: 1.5em;
            text-shadow: 0 0 15px #00b3ff;
        }
        .name {
            font-size: 1.8em;
            color: #00b3ff;
            text-shadow: 0 0 15px #00b3ff;
            margin-left: 20px;
            font-style: italic;
        }
        .background-effects {
            position: absolute;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            background: url('https://i.postimg.cc/pXXHqkXr/1742316301125-2.jpg') no-repeat center center;
            background-size: cover;
            filter: blur(5px);
            z-index: -1;
            opacity: 0.5; /* Hacer que el fondo no opaque el contenido */
        }
    </style>
</head>
<body>
    <div class="background-effects"></div>
    <h1>Bienvenido a mi mundo - Anth'Zz Berrocal</h1>
    <div class="score-container">
        <span class="score-label">Puntos:</span> <span id="score">0</span>
        <span class="name">Anth'Zz Berrocal</span>
    </div>
    <div class="game-container" id="game">
        <div class="catcher" id="catcher"></div>
    </div>
    <script>
        const game = document.getElementById('game');
        const catcher = document.getElementById('catcher');
        const scoreDisplay = document.getElementById('score');
        let score = 0;

        function spawnPhoto() {
            const photo = document.createElement('img');
            photo.src = 'https://i.postimg.cc/pXXHqkXr/1742316301125-2.jpg';
            photo.classList.add('falling-photo');
            photo.style.left = Math.random() * 95 + 'vw';
            photo.addEventListener('click', () => {
                score++;
                scoreDisplay.textContent = score;
                photo.remove();
            });
            game.appendChild(photo);
            setTimeout(() => photo.remove(), 6000);
        }

        function moveCatcher(e) {
            const x = e.touches ? e.touches[0].clientX - 75 : e.clientX - 75;
            catcher.style.left = `${x}px`;
        }

        document.addEventListener('mousemove', moveCatcher);
        document.addEventListener('touchmove', moveCatcher);
        setInterval(spawnPhoto, 1000);
    </script>
</body>
</html>
