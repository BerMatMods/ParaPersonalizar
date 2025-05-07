<!DOCTYPE html><html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>¡Feliz Día Mamita!</title>
  <link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Poppins:wght@400;600&display=swap" rel="stylesheet">
  <style>
    * {
      margin: 0; padding: 0;
      box-sizing: border-box;
      font-family: 'Poppins', sans-serif;
    }
    body {
      background: linear-gradient(135deg, #ffe6f0, #ffd9ec);
      color: #333;
      overflow-x: hidden;
    }
    .pantalla {
      width: 100vw; height: 100vh;
      display: flex; flex-direction: column;
      align-items: center; justify-content: center;
      text-align: center;
      padding: 2rem;
      position: relative;
    }
    h1 {
      font-family: 'Great Vibes', cursive;
      font-size: 3rem;
      color: #d63384;
      margin-bottom: 1rem;
    }
    .mensaje {
      font-size: 1.2rem;
      background: #fff;
      padding: 1.5rem;
      border-radius: 20px;
      box-shadow: 0 0 20px rgba(255,105,180,0.4);
      max-width: 600px;
      margin-bottom: 2rem;
      line-height: 1.6;
    }
    .boton {
      padding: 0.8rem 1.5rem;
      font-size: 1rem;
      background: #ff69b4;
      color: white;
      border: none;
      border-radius: 30px;
      cursor: pointer;
      transition: transform 0.2s;
    }
    .boton:hover {
      transform: scale(1.1);
    }
    .flor {
      position: absolute;
      bottom: 0;
      animation: crecer 4s ease-out forwards;
      width: 100px;
    }
    @keyframes crecer {
      from { transform: scaleY(0); }
      to { transform: scaleY(1); }
    }
    .redes {
      margin-top: 2rem;
      display: flex;
      gap: 1rem;
      flex-wrap: wrap;
      justify-content: center;
    }
    .redes a {
      text-decoration: none;
      font-weight: bold;
      display: flex;
      align-items: center;
      gap: 0.5rem;
      background: #fff;
      padding: 0.6rem 1rem;
      border-radius: 15px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
      transition: all 0.3s;
    }
    .redes a:hover {
      transform: scale(1.1);
      background: #ffe0f0;
    }
    .creador {
      margin-top: 2rem;
      font-size: 0.9rem;
      color: #888;
    }
  </style>
</head>
<body>  <div class="pantalla" id="pantalla1">
    <h1>¡Feliz Día Mamita!</h1>
    <div class="mensaje">
      Gracias por cada sonrisa, por cada consejo, por tu paciencia infinita y por tu amor que nunca falla. <br>
      Eres el corazón de esta familia, la reina de nuestras vidas y la luz que siempre guía nuestros pasos. <br>
      Hoy celebramos no solo a la madre, sino a la mujer maravillosa que eres. <br>
      ¡Te amo con todo mi ser, mamá!
    </div>
    <button class="boton" onclick="siguientePantalla()">Ver Sorpresa</button>
  </div>  <div class="pantalla" id="pantalla2" style="display: none;">
    <h1>¡Te Mereces Todo Mamita!</h1>
    <div class="mensaje">
      Hoy florece esta flor para ti, como símbolo de todo el amor que sembraste en mi corazón. <br>
      Que este día te llene de alegría, orgullo y amor. <br>
      ¡Gracias por ser mi guía, mi fuerza y mi inspiración cada día!
    </div>
    <img class="flor" src="https://i.imgur.com/ntqbTqW.png" alt="Flor animada">
    <div class="creador">
      Creado con amor por <strong>Anth'Zz Berrocal | BerMatModZ</strong>
    </div>
    <div class="redes">
      <a href="https://youtube.com/@bermatmodz" target="_blank">YouTube</a>
      <a href="https://github.com/bermatmods" target="_blank">GitHub</a>
      <a href="https://facebook.com/anthzzberrocal" target="_blank">Facebook</a>
      <a href="https://instagram.com/bermatmodz" target="_blank">Instagram</a>
      <a href="https://wa.me/51937556459" target="_blank">WhatsApp</a>
      <a href="https://t.me/bermatmodz" target="_blank">Telegram</a>
    </div>
  </div>  <script>
    function siguientePantalla() {
      document.getElementById("pantalla1").style.display = "none";
      document.getElementById("pantalla2").style.display = "flex";
    }
  </script></body>
</html>
