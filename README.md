<!DOCTYPE html><html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Feliz Día Mamá</title>
  <link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Orbitron:wght@600&family=Roboto&display=swap" rel="stylesheet">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    body {
      font-family: 'Roboto', sans-serif;
      background: linear-gradient(135deg, #ffdde1 0%, #ee9ca7 100%);
      overflow-x: hidden;
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
    #pantalla2 { display: none; }.flor-contenedor {
  position: absolute;
  bottom: -100px;
  animation: crecerFlor 3s ease-out forwards;
}
.flor {
  width: 100px;
  height: 100px;
  background: radial-gradient(circle, pink 40%, deeppink);
  border-radius: 50%;
  box-shadow: 0 0 25px #ff1493;
}
@keyframes crecerFlor {
  to { bottom: 150px; }
}

.boton {
  background: #ff1493;
  color: white;
  padding: 15px 40px;
  border: none;
  border-radius: 50px;
  font-size: 1.4rem;
  font-family: 'Orbitron', sans-serif;
  box-shadow: 0 0 20px #ff1493;
  cursor: pointer;
  animation: brillar 2s infinite;
  margin-top: 60px;
}
@keyframes brillar {
  0%, 100% { box-shadow: 0 0 20px #ff1493; }
  50% { box-shadow: 0 0 40px #ff69b4; }
}

.mensaje {
  text-align: center;
  max-width: 800px;
  background: rgba(255, 255, 255, 0.9);
  padding: 40px;
  border-radius: 30px;
  box-shadow: 0 0 20px #ffc0cb;
  animation: aparecer 1.5s ease-in;
}
@keyframes aparecer {
  0% { transform: scale(0.8); opacity: 0; }
  100% { transform: scale(1); opacity: 1; }
}
.mensaje h1 {
  font-family: 'Great Vibes', cursive;
  font-size: 3rem;
  color: #c2185b;
  margin-bottom: 20px;
}
.mensaje p {
  font-size: 1.3rem;
  line-height: 1.6;
  color: #880e4f;
}

.creditos {
  margin-top: 40px;
  font-family: 'Orbitron', sans-serif;
  background: #fff0f5;
  padding: 10px 30px;
  border-radius: 20px;
  box-shadow: 0 0 10px deeppink;
  color: #ff1493;
}

.redes {
  margin-top: 30px;
  display: flex;
  justify-content: center;
  gap: 25px;
  flex-wrap: wrap;
}
.redes a {
  text-decoration: none;
  display: flex;
  align-items: center;
  gap: 10px;
  background: white;
  padding: 10px 15px;
  border-radius: 20px;
  box-shadow: 0 0 10px #ffb6c1;
  font-weight: bold;
  color: #d81b60;
  transition: transform 0.3s;
}
.redes a:hover {
  transform: scale(1.1);
  background: #ffe0ec;
}
.redes img {
  width: 24px;
  height: 24px;
}

  </style>
</head>
<body>
  <div id="pantalla1" class="pantalla">
    <div class="flor-contenedor">
      <div class="flor"></div>
    </div>
    <button class="boton" onclick="mostrarMensaje()">Haz clic para ver la sorpresa</button>
  </div>  <div id="pantalla2" class="pantalla">
    <div class="mensaje">
      <h1>¡Feliz Día Mamita!</h1>
      <p>Gracias por cada sonrisa, por cada consejo, por tu paciencia infinita y por tu amor que nunca falla. Eres el corazón de esta familia, la reina de nuestras vidas y la luz que siempre guía nuestros pasos. Hoy celebramos no solo a la madre, sino a la mujer maravillosa que eres. ¡Te amo con todo mi ser, mamá!</p>
      <div class="creditos">Creado con amor por Anth'Zz Berrocal | BerMatModZ</div>
      <div class="redes">
        <a href="https://youtube.com/@bermatmods"><img src="https://cdn-icons-png.flaticon.com/512/1384/1384060.png">YouTube</a>
        <a href="https://github.com/Anthzberrocal"><img src="https://cdn-icons-png.flaticon.com/512/733/733553.png">GitHub</a>
        <a href="https://facebook.com/anthzberrocal"><img src="https://cdn-icons-png.flaticon.com/512/733/733547.png">Facebook</a>
        <a href="https://instagram.com/bermatmods"><img src="https://cdn-icons-png.flaticon.com/512/2111/2111463.png">Instagram</a>
        <a href="https://wa.me/51937556459"><img src="https://cdn-icons-png.flaticon.com/512/733/733585.png">WhatsApp</a>
        <a href="https://t.me/bermatmods"><img src="https://cdn-icons-png.flaticon.com/512/2111/2111646.png">Telegram</a>
      </div>
    </div>
  </div>  <script>
    function mostrarMensaje() {
      document.getElementById('pantalla1').style.display = 'none';
      document.getElementById('pantalla2').style.display = 'flex';
    }
  </script></body>
</html>
