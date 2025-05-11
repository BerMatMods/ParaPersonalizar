<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mi Mundo - Anth'Zz Berrocal</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;600&family=Orbitron:wght@400;500&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            background: linear-gradient(135deg, #000000, #00b3ff); /* Fondo negro a celeste */
            font-family: 'Poppins', sans-serif;
            color: #fff;
            overflow: hidden;
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            position: relative;
        }
        h1 {
            font-size: 3.5em;
            color: #00b3ff;
            text-align: center;
            margin-bottom: 20px;
            text-shadow: 0 0 15px rgba(0, 179, 255, 0.9);
            font-family: 'Orbitron', sans-serif;
            font-style: italic;
        }
        .banner {
            background-color: rgba(0, 0, 0, 0.7);
            padding: 15px;
            border-radius: 12px;
            margin-bottom: 30px;
            box-shadow: 0 0 15px rgba(0, 179, 255, 0.8);
            width: 90%;
            max-width: 600px;
            text-align: center;
            font-size: 1.5em;
            color: #00b3ff;
            font-family: 'Orbitron', sans-serif;
        }
        .game-container {
            position: relative;
            width: 80vw;
            height: 60vh;
            overflow: hidden;
            border-radius: 20px;
            background-color: rgba(0, 0, 0, 0.7);
            box-shadow: 0 0 50px #00b3ff;
            margin-bottom: 30px;
        }
        .catcher {
            position: absolute;
            bottom: 20px;
            width: 120px;
            height: 40px;
            background-color: #00b3ff;
            border-radius: 20px;
            transition: all 0.2s ease;
            box-shadow: 0 0 15px #00b3ff;
        }
        .falling-photo {
            position: absolute;
            width: 120px;
            height: 120px;
            border-radius: 50%;
            animation: fall 6s linear infinite;
            border: 3px solid #fff;
        }
        @keyframes fall {
            0% { top: -120px; }
            100% { top: 100%; }
        }
        .score-container {
            font-size: 1.8em;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #00b3ff;
            text-shadow: 0 0 10px #00b3ff;
            margin-bottom: 15px;
        }
        .name {
            font-size: 1.8em;
            color: #00b3ff;
            text-shadow: 0 0 10px #00b3ff;
            font-family: 'Orbitron', sans-serif;
            font-style: italic;
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
        .score-box {
            background-color: rgba(0, 0, 0, 0.7);
            padding: 10px 20px;
            border-radius: 12px;
            box-shadow: 0 0 10px rgba(0, 179, 255, 0.9);
            margin-top: 20px;
            font-family: 'Poppins', sans-serif;
            font-size: 1.6em;
        }
    </style>
</head>
<body>
    <h1>Mi Mundo - Anth'Zz Berrocal</h1>
    <div class="banner">
        ¡Bienvenido al juego de fotos de mi amor! ¡Ayuda a atrapar las fotos mientras caen! 
    </div>
    <div class="score-container">
        <span id="score">Puntos: 0</span>
        <span class="name">Anth'Zz Berrocal</span>
    </div>
    <div class="game-container" id="game">
        <div class="catcher" id="catcher"></div>
    </div>
    <div class="score-box">
        <span id="score-box">Puntos: 0</span>
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
            photo.style.left = Math.random() * (game.clientWidth - 120) + 'px';
            photo.addEventListener('click', () => {
                score++;
                scoreDisplay.textContent = 'Puntos: ' + score;
                photo.remove();
            });
            game.appendChild(photo);
            setTimeout(() => photo.remove(), 6000);
        }

        function moveCatcher(e) {
            const x = e.touches ? e.touches[0].clientX - 75 : e.clientX - 75;
            catcher.style.left = `${x}px`;
            cursor.style.left = `${x - 25}px`;
        }

        document.addEventListener('mousemove', moveCatcher);
        document.addEventListener('touchmove', moveCatcher);
        setInterval(spawnPhoto, 1000);
    </script>
</body>
</html>
