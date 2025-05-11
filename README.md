<!DOCTYPE html><html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BerMat-Games</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;600&family=Orbitron:wght@400;500&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            background: linear-gradient(135deg, #000000, #00b3ff);
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
            font-size: 4em;
            color: #00b3ff;
            text-align: center;
            margin-bottom: 20px;
            text-shadow: 0 0 15px rgba(0, 179, 255, 0.9);
            font-family: 'Orbitron', sans-serif;
            font-style: italic;
            background: rgba(0, 0, 0, 0.7);
            padding: 15px 30px;
            border-radius: 15px;
            box-shadow: 0 0 20px #00b3ff;
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
    </style>
</head>
<body>
    <h1>🌀 BerMat-Games 🌀</h1>
    <div class="game-container" id="game">
        <div class="catcher" id="catcher"></div>
    </div>
    <script>
        const game = document.getElementById('game');
        const catcher = document.getElementById('catcher');
        let score = 0;function spawnPhoto() {
        const photo = document.createElement('img');
        photo.src = 'https://i.postimg.cc/pXXHqkXr/1742316301125-2.jpg';
        photo.classList.add('falling-photo');
        photo.style.left = Math.random() * (game.clientWidth - 120) + 'px';
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
