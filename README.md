<!DOCTYPE html><html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Juego Épico de BerMatModZ</title>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500&display=swap" rel="stylesheet">
    <style>
        body {
            margin: 0;
            font-family: 'Orbitron', sans-serif;
            background: radial-gradient(circle, #000, #111, #222, #000);
            color: #0f0;
            overflow: hidden;
        }
        header {
            background: linear-gradient(90deg, #0f0, #00f, #f0f);
            padding: 20px;
            text-align: center;
            animation: glow 2s infinite alternate;
            box-shadow: 0 0 30px #0f0;
            border-radius: 20px;
            margin: 20px auto;
            width: 90%;
        }
        @keyframes glow {
            0% { color: #0f0; text-shadow: 0 0 5px #0f0, 0 0 15px #0f0; }
            100% { color: #fff; text-shadow: 0 0 15px #00f, 0 0 30px #f0f; }
        }
        .game-container {
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            height: calc(100vh - 160px);
            gap: 20px;
        }
        .game-box {
            background: rgba(15, 15, 15, 0.95);
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 0 20px #0f0, 0 0 40px #00f;
            animation: flicker 1.5s infinite alternate;
            text-align: center;
            width: 80%;
        }
        @keyframes flicker {
            0% { opacity: 0.8; }
            100% { opacity: 1; }
        }
        button {
            background: #0f0;
            color: #000;
            border: none;
            padding: 15px 30px;
            border-radius: 10px;
            font-size: 18px;
            cursor: pointer;
            transition: all 0.3s;
            box-shadow: 0 0 10px #0f0, 0 0 20px #00f;
        }
        button:hover {
            background: #00f;
            color: #fff;
            box-shadow: 0 0 20px #f0f, 0 0 40px #0f0;
        }
        #gameOutput {
            margin-top: 20px;
            color: #0f0;
            font-size: 18px;
            text-shadow: 0 0 5px #0f0;
        }
    </style>
</head>
<body>
    <header>
        <h1>⚡ BerMatModZ - Juego Épico 🔥</h1>
        <p>Bienvenido al universo hacker de BerMatModZ</p>
    </header>
    <div class="game-container">
        <div class="game-box">
            <h2>Desafío Hacker</h2>
            <p>Pulsa el botón para iniciar el juego:</p>
            <button onclick="startGame()">Iniciar</button>
            <div id="gameOutput"></div>
        </div>
    </div>
    <script>
        function startGame() {
            const output = document.getElementById("gameOutput");
            output.textContent = "🔓 Accediendo a la red de BerMatModZ...";
            setTimeout(() => {
                output.textContent = "🛡️ Bienvenido al desafío. ¿Estás listo para hackear el sistema?";
            }, 2000);
        }
    </script>
</body>
</html>
