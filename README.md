<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Feliz Día Mamá</title>
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', sans-serif;
      background: linear-gradient(to bottom, #ffe6f0, #ffffff);
      overflow: hidden;
    }
    .pantalla {
      position: absolute;
      width: 100%;
      height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      transition: opacity 1s ease-in-out;
    }
    #pantalla2 { display: none; }

    .boton {
      background: #ff69b4;
      color: white;
      padding: 15px 30px;
      border: none;
      border-radius: 30px;
      font-size: 1.2rem;
      box-shadow: 0 0 10px #ff69b4;
      cursor: pointer;
      animation: pulse 2s infinite;
    }
    @keyframes pulse {
      0% { box-shadow: 0 0 10px #ff69b4; }
      50% { box-shadow: 0 0 20px #ff1493; }
      100% { box-shadow: 0 0 10px #ff69b4; }
    }

    .flor {
      width: 100px;
      height: 100px;
      background: radial-gradient(circle, pink 40%, hotpink);
      border-radius: 50%;
      animation: crecer 3s ease-out forwards;
      transform: scale(0);
    }
    @keyframes crecer {
      to { transform: scale(1); }
    }

    .mensaje {
      text-align: center;
      font-size: 1.6rem;
      color: #d60087;
      padding: 20px;
      max-width: 700px;
      animation: aparecer 2s ease-in;
    }

    .corazones {
      position: absolute;
      bottom: 20px;
      font-size: 2rem;
      animation: flotar 4s infinite ease-in-out;
    }
    @keyframes flotar {
      0% { transform: translateY(0); opacity: 1; }
      100% { transform: translateY(-30px); opacity: 0.5; }
    }

    .creditos {
      margin-top: 30px;
      font-size: 1rem;
      color: #555;
      font-weight: bold;
      background: #fff0f5;
      padding: 10px 20px;
      border-radius: 20px;
      box-shadow: 0 0 10px pink;
    }
  </style>
</head>
<body>
  <div id="pantalla1" class="pantalla">
    <div class="flor"></div>
    <button class="boton" onclick="mostrarMensaje()">Haz clic para ver la sorpresa</button>
  </div>

  <div id="pantalla2" class="pantalla">
    <div class="mensaje">
      <h1>¡Feliz Día Mamita!</h1>
      <p>Gracias por tu amor infinito, tu apoyo incondicional y tu corazón tan fuerte y hermoso. Eres la reina de mi vida. ¡Te amo con todo mi ser!</p>
    </div>
    <div class="corazones">❤️❤️❤️❤️❤️</div>
    <div class="creditos">Creado con amor por Anth'Zz Berrocal | BerMatModZ</div>
  </div>

  <script>
    function mostrarMensaje() {
      document.getElementById('pantalla1').style.display = 'none';
      document.getElementById('pantalla2').style.display = 'flex';
    }
  </script>
</body>
</html>
