<!DOCTYPE html><html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Corazón Animado - BerMatModZ</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background-color: #0f0f0f;
            color: #ffffff;
            font-family: 'Courier New', Courier, monospace;
            overflow: hidden;
        }
        .heart-container {
            position: relative;
            width: 250px;
            height: 250px;
            animation: float 5s ease-in-out infinite alternate;
        }
        .heart {
            width: 100%;
            height: 100%;
            background-color: #ff007f;
            position: absolute;
            top: 0;
            left: 0;
            clip-path: polygon(50% 0%, 100% 35%, 80% 100%, 50% 85%, 20% 100%, 0% 35%);
            animation: heartbeat 1.5s ease-in-out infinite;
        }
        .text-container {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            text-align: center;
            color: #ffffff;
            font-weight: bold;
            font-size: 18px;
            line-height: 1.5;
        }
        .text-container h1 {
            color: #ffd700;
            font-size: 24px;
            margin: 0;
        }
        @keyframes heartbeat {
            0%, 100% { transform: scale(1); }
            25% { transform: scale(1.1); }
            50% { transform: scale(0.9); }
            75% { transform: scale(1.2); }
        }
        @keyframes float {
            0% { transform: translateY(0px); }
            100% { transform: translateY(-20px); }
        }
        .flower {
            position: absolute;
            bottom: -60px;
            width: 50px;
            animation: grow 5s infinite alternate ease-in-out;
        }
        .flower:nth-child(1) { left: 20%; animation-delay: 0s; }
        .flower:nth-child(2) { left: 50%; animation-delay: 2s; }
        .flower:nth-child(3) { left: 80%; animation-delay: 4s; }
        @keyframes grow {
            0% { transform: scale(0) translateY(100px); opacity: 0; }
            50% { transform: scale(1) translateY(-30px); opacity: 1; }
            100% { transform: scale(1.2) translateY(-60px); opacity: 0.8; }
        }
    </style>
</head>
<body>
    <div class="heart-container">
        <div class="heart"></div>
        <div class="text-container">
            <h1>⚡ BerMatModZ ⚡</h1>
            <p>Programador | Hacker | Ciberseguridad</p>
            <p>Proyectos: BerMat_Bot, BerMatMods, ⚡BerMat-Bot MD🔥</p>
            <p>Contacta: Anth'Zz Berrocal</p>
            <p>WhatsApp: 937556459</p>
            <p>Ubicación: Andahuaylas</p>
        </div>
        <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/a/a0/Rose_icon.svg/1200px-Rose_icon.svg.png" class="flower" alt="Flor 1">
        <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/a/a0/Rose_icon.svg/1200px-Rose_icon.svg.png" class="flower" alt="Flor 2">
        <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/a/a0/Rose_icon.svg/1200px-Rose_icon.svg.png" class="flower" alt="Flor 3">
    </div>
</body>
</html>
