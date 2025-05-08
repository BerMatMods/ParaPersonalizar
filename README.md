<!DOCTYPE html><html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BerMatModZ - Dashboard</title>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@700&family=Roboto+Mono:wght@500&family=VT323&display=swap" rel="stylesheet">
    <style>
        body {
            background-color: #000000;
            color: #00ff00;
            font-family: 'VT323', monospace;
            background-image: radial-gradient(circle, #010101, #020202, #050505, #080808, #0b0b0b, #0f0f0f, #121212, #151515, #191919, #1c1c1c, #1f1f1f, #222222);
            overflow: hidden;
            margin: 0;
            padding: 0;
            transition: background-color 0.5s, color 0.5s;
        }
        .background-animation {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            background: url('https://media.giphy.com/media/Rmw2fYg7sfuFWnshjV/giphy.gif') center/cover no-repeat;
            opacity: 0.15;
            filter: blur(3px) brightness(1.2);
        }
        .container {
            width: 90%;
            max-width: 800px;
            margin: 50px auto;
            padding: 20px;
            background-color: rgba(0, 0, 0, 0.95);
            border-radius: 20px;
            box-shadow: 0 0 30px #00ff00, 0 0 60px #ff0000;
            border: 2px solid #00ff00;
            text-align: center;
            z-index: 1;
            position: relative;
        }
        h1 {
            color: #ff0000;
            font-family: 'Orbitron', sans-serif;
            font-size: 3em;
            margin-bottom: 20px;
            text-shadow: 0 0 20px #00ff00, 0 0 40px #ff0000, 0 0 60px #0000ff;
            animation: neon 2s infinite alternate;
        }
        @keyframes neon {
            0% { text-shadow: 0 0 30px #00ff00, 0 0 60px #ff0000, 0 0 90px #0000ff; }
            100% { text-shadow: 0 0 50px #ff0000, 0 0 80px #00ff00, 0 0 120px #0000ff; }
        }
        .dashboard-card {
            background-color: rgba(0, 0, 0, 0.8);
            padding: 20px;
            margin-bottom: 30px;
            border-radius: 15px;
            box-shadow: 0 0 20px #ff0000, 0 0 40px #00ff00;
            text-align: left;
            font-family: 'Roboto Mono', monospace;
            border: 2px solid #ff0000;
        }
        .dashboard-card h2 {
            color: #00ff00;
            font-size: 1.8em;
            margin-bottom: 15px;
            text-shadow: 0 0 10px #ff0000;
        }
        .dashboard-card p {
            color: #00ff00;
            font-size: 1.2em;
            line-height: 1.6em;
        }
        .dashboard-card a {
            color: #ff0000;
            font-size: 1.2em;
            text-decoration: none;
            padding: 10px;
            border-radius: 10px;
            border: 2px solid #ff0000;
            transition: 0.3s;
        }
        .dashboard-card a:hover {
            background-color: #ff0000;
            color: #fff;
            box-shadow: 0 0 20px #ff0000;
        }
        .footer {
            margin-top: 30px;
            color: #fff;
            font-size: 0.8em;
            font-family: 'Roboto Mono', monospace;
        }
    </style>
</head>
<body>
    <div class="background-animation"></div>
    <div class="container">
        <h1>⚡ Bienvenido a BerMatModZ Dashboard ⚡</h1>
        <div class="dashboard-card">
            <h2>🧑‍💻 Proyectos Actuales:</h2>
            <p>- ⚡ **BerMat-Bot MD🔥** - Bot de WhatsApp con IA avanzada.</p>
            <p>- 🔥 **BerMatModZ** - Sistema de automatización con Python y Termux.</p>
            <p>- 💻 **Simulación de Hackeo** - Herramientas de hacking personalizadas.</p>
            <a href="#">Ver más</a>
        </div>
        <div class="dashboard-card">
            <h2>🔒 Acceso Exclusivo:</h2>
            <p>Solo para miembros registrados. Obtén acceso a contenido y herramientas avanzadas de **BerMatModZ**.</p>
            <a href="#">Ver contenido exclusivo</a>
        </div>
        <div class="footer">© 2025 BerMatModZ - Todos los derechos reservados</div>
    </div>
</body>
</html>
