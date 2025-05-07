<!DOCTYPE html><html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BerMatModZ - Dino Runner</title>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@600&display=swap" rel="stylesheet">
    <style>
        body {
            margin: 0;
            font-family: 'Orbitron', sans-serif;
            background: radial-gradient(circle, #000, #111, #222, #000);
            color: #0f0;
            overflow: hidden;
            display: flex;
            flex-direction: column;
            align-items: center;
            height: 100vh;
            justify-content: center;
        }
        header {
            background: linear-gradient(90deg, #0f0, #00f, #f0f);
            padding: 20px;
            text-align: center;
            border-radius: 20px;
            margin-bottom: 20px;
            width: 90%;
            animation: glow 2s infinite alternate;
            box-shadow: 0 0 30px #0f0;
        }
        @keyframes glow {
            0% { color: #0f0; text-shadow: 0 0 5px #0f0, 0 0 15px #0f0; }
            100% { color: #fff; text-shadow: 0 0 15px #00f, 0 0 30px #f0f; }
        }
        .game-container {
            position: relative;
            width: 80%;
            height: 300px;
            background: #111;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 0 20px #0f0, 0 0 40px #00f;
        }
        .dino {
            width: 50px;
            height: 50px;
            background: #0f0;
            position: absolute;
            bottom: 10px;
            left: 20px;
            border-radius: 10px;
            animation: flicker 1s infinite alternate;
        }
        @keyframes flicker {
            0% { opacity: 0.8; }
            100% { opacity: 1; }
        }
        .obstacle {
            width: 30px;
            height: 50px;
            background: #f00;
            position: absolute;
            bottom: 10px;
            right: 0;
            animation: move 2s linear infinite;
        }
        @keyframes move {
            0% { right: 0; }
            100% { right: 100%; }
        }
    </style>
</head>
<body>
    <header>
        <h1>⚡ BerMatModZ - Dino Runner 🔥</h1>
        <p>El juego infinito de BerMatModZ</p>
    </header>
    <div class="game-container">
        <div class="dino" id="dino"></div>
        <div class="obstacle" id="obstacle"></div>
    </div>
    <script>
        const dino = document.getElementById('dino');
        const obstacle = document.getElementById('obstacle');
        let isJumping = false;function jump() {
        if (isJumping) return;
        isJumping = true;
        let position = 0;
        const upInterval = setInterval(() => {
            if (position >= 150) {
                clearInterval(upInterval);
                const downInterval = setInterval(() => {
                    if (position <= 0) {
                        clearInterval(downInterval);
                        isJumping = false;
                    }
                    position -= 20;
                    dino.style.bottom = position + 'px';
                }, 20);
            }
            position += 20;
            dino.style.bottom = position + 'px';
        }, 20);
    }

    function checkCollision() {
        const dinoRect = dino.getBoundingClientRect();
        const obstacleRect = obstacle.getBoundingClientRect();
        if (
            dinoRect.right > obstacleRect.left &&
            dinoRect.left < obstacleRect.right &&
            dinoRect.bottom > obstacleRect.top
        ) {
            alert('💀 Game Over - Eres un Hacker Épico, BerMatModZ 💥');
            location.reload();
        }
    }

    document.addEventListener('keydown', jump);
    setInterval(checkCollision, 20);
</script>

</body>
</html>
