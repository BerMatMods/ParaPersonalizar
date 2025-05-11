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
            border: 2px solid #00ff88;
            margin: 20px 0;
        }
        .catcher {
            position: absolute;
            bottom: 0;
            width: 100px;
            height: 100px;
            background-color: #00ff88;
            border-radius: 50%;
            filter: drop-shadow(0 0 10px #00ff88);
        }
        .falling-photo {
            position: absolute;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            animation: fall 6s linear infinite;
        }
        @keyframes fall {
            0% { top: -50px; }
            100% { top: 90vh; }
        }
        .score {
            font-size: 2em;
            color: #ff0;
            text-shadow: 0 0 10px #ff0, 0 0 20px #ff0;
        }
    </style>
</head>
<body>
    <h1>Bienvenido a mi mundo - Anth'Zz Berrocal</h1>
    <div class="score">Puntos: <span id="score">0</span></div>
    <div class="game-container" id="game">
        <div class="catcher" id="catcher"></div>
    </div>
    <script>
        const game = document.getElementById('game');
        const catcher = document.getElementById('catcher');
        const scoreDisplay = document.getElementById('score');
        let score = 0;function spawnPhoto() {
        const photo = document.createElement('img');
        photo.src = 'https://i.postimg.cc/D0SSGhDk/Mag-Pic-20250211-191544901-2.jpg'; // Reemplaza con fotos de tu novia
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
        const x = e.clientX - 50;
        catcher.style.left = `${x}px`;
    }

    document.addEventListener('mousemove', moveCatcher);
    setInterval(spawnPhoto, 1000);
</script>

</body>
</html>
