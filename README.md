<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mi Mundo - Anth'Zz Berrocal</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;600&family=Orbitron:wght@400;500&display=swap" rel="stylesheet">
    <style>
        body {
            margin: 0;
            padding: 0;
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(135deg, #212121, #1c1c1c, #0a0a0a);
            color: #00ff88;
            overflow: hidden;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }
        h1 {
            font-size: 4em;
            color: #00b3ff;
            text-align: center;
            text-shadow: 0 0 15px #00b3ff, 0 0 30px #00b3ff;
            margin-bottom: 20px;
            font-family: 'Orbitron', sans-serif;
            letter-spacing: 5px;
        }
        .game-container {
            position: relative;
            width: 100vw;
            height: 70vh;
            overflow: hidden;
            border: 5px solid #00b3ff;
            border-radius: 20px;
            box-shadow: 0 0 50px #00b3ff;
            background-color: rgba(0, 0, 0, 0.6);
        }
        .catcher {
            position: absolute;
            bottom: 20px;
            width: 180px;
            height: 50px;
            background-color: #00b3ff;
            border-radius: 25px;
            filter: drop-shadow(0 0 15px #00b3ff);
            box-shadow: 0 0 20px #00b3ff;
            transition: all 0.2s ease;
        }
        .falling-photo {
            position: absolute;
            width: 120px;
            height: 120px;
            border-radius: 15px;
            border: 3px solid #fff;
            animation: fall 6s linear infinite;
        }
        @keyframes fall {
            0% { top: -120px; }
            100% { top: 90vh; }
        }
        .score-container {
            font-size: 2.5em;
            color: #00ffcc;
            text-shadow: 0 0 20px #00ffcc, 0 0 30px #00ffcc;
            margin-bottom: 10px;
            display: flex;
            align-items: center;
        }
        .score-label {
            margin-right: 10px;
            font-family: 'Orbitron', sans-serif;
            font-size: 1.5em;
            color: #00b3ff;
            text-shadow: 0 0 15px #00b3ff;
        }
        .name {
            font-size: 2em;
            color: #00b3ff;
            text-shadow: 0 0 20px #00b3ff;
            margin-left: 20px;
            font-family: 'Orbitron', sans-serif;
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
            opacity: 0.5;
        }
        .cursor {
            width: 50px;
            height: 50px;
            background-color: rgba(0, 179, 255, 0.7);
            border-radius: 50%;
            position: absolute;
            pointer-events: none;
            transition: transform 0.1s ease;
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
    <div class="cursor" id="cursor"></div>
    <script>
        const game = document.getElementById('game');
        const catcher = document.getElementById('catcher');
        const scoreDisplay = document.getElementById('score');
        const cursor = document.getElementById('cursor');
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
            const x = e.touches ? e.touches[0].clientX - 90 : e.clientX - 90;
            catcher.style.left = `${x}px`;
            cursor.style.left = `${x - 25}px`;
        }

        document.addEventListener('mousemove', moveCatcher);
        document.addEventListener('touchmove', moveCatcher);
        setInterval(spawnPhoto, 1000);
    </script>
</body>
</html>
