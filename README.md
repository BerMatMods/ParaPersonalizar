<!DOCTYPE html><html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mi Mundo - Anth'Zz Berrocal</title>
    <style>
        body {
            background: linear-gradient(135deg, #0d0d0d, #1a1a1a, #333);
            color: #0f0;
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
            color: #00ff88;
            text-shadow: 0 0 15px #00ff88, 0 0 30px #00ff88;
        }
        .game-container {
            position: relative;
            width: 100vw;
            height: 80vh;
            overflow: hidden;
            border: 3px solid #00ff88;
            border-radius: 20px;
            margin: 20px 0;
            box-shadow: 0 0 30px #00ff88;
        }
        .catcher {
            position: absolute;
            bottom: 20px;
            width: 150px;
            height: 40px;
            background-color: #00ff88;
            border-radius: 20px;
            filter: drop-shadow(0 0 10px #00ff88);
            border: 2px solid #fff;
        }
        .falling-photo {
            position: absolute;
            width: 80px;
            height: 80px;
            border-radius: 15px;
            border: 3px solid #fff;
            filter: drop-shadow(0 0 10px #ff69b4);
            animation: fall 6s linear infinite;
        }
        @keyframes fall {
            0% { top: -80px; }
            100% { top: 90vh; }
        }
        .score-container {
            font-size: 2em;
            color: #ff0;
            text-shadow: 0 0 10px #ff0, 0 0 20px #ff0;
            margin-bottom: 10px;
            display: flex;
            align-items: center;
        }
        .score-label {
            margin-right: 10px;
            color: #00ff88;
            font-size: 1.2em;
            text-shadow: 0 0 10px #00ff88;
        }
        .name {
            font-size: 1.5em;
            color: #00ff88;
            text-shadow: 0 0 10px #00ff88;
            margin-left: 20px;
        }
    </style>
</head>
<body>
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
        let score = 0;function spawnPhoto() {
        const photo = document.createElement('img');
        photo.src = 'https://i.postimg.cc/D0SSGhDk/Mag-Pic-20250211-191544901-2.jpg';
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
