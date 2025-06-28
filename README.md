<!DOCTYPE html><html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>🎉 Sorpresa Aniversario para Mi Reina</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Great+Vibes&family=Orbitron:wght@600&display=swap');body {
  margin: 0;
  padding: 0;
  background: linear-gradient(135deg, #fbc2eb 0%, #a6c1ee 100%);
  font-family: 'Orbitron', sans-serif;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  color: #fff;
  text-align: center;
  overflow: hidden;
}

h1 {
  font-size: 3em;
  margin: 0.2em 0;
  text-shadow: 0 0 15px #fff;
}

.contador {
  font-size: 2em;
  margin: 10px;
  animation: glow 2s ease-in-out infinite alternate;
}

.boton {
  margin-top: 20px;
  padding: 15px 25px;
  background-color: #ff69b4;
  border: none;
  border-radius: 12px;
  color: white;
  font-size: 1.2em;
  cursor: pointer;
  transition: 0.3s;
  text-decoration: none;
  animation: flotar 2s infinite ease-in-out;
  box-shadow: 0 0 15px #ff1493;
}

.boton:hover {
  background-color: #ff1493;
}

@keyframes glow {
  from {
    text-shadow: 0 0 10px #fff, 0 0 20px #ff6ec4, 0 0 30px #ff6ec4;
  }
  to {
    text-shadow: 0 0 20px #fff, 0 0 30px #ff1493, 0 0 40px #ff1493;
  }
}

@keyframes flotar {
  0%, 100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-10px);
  }
}

.hidden {
  display: none;
}

.carta {
  font-family: 'Great Vibes', cursive;
  font-size: 1.8em;
  margin-top: 30px;
  max-width: 80%;
  color: #fff5f8;
  text-shadow: 0 0 10px #ffb6c1;
}

  </style>
</head>
<body>
  <h1>💘 FELIZ ANIVERSARIO MI REINA 💘</h1>
  <div class="contador" id="tiempo1"></div>
  <div class="contador hidden" id="tiempo2"></div>
  <a href="#" class="boton" onclick="mostrarTiempo()">✨ Haz click aquí mi mami ✨</a>  <div class="carta">
    Mi amor, desde que llegaste a mi vida<br>
    todo es más bonito. Gracias por cada sonrisa,<br>
    por cada momento, por ser tú. Te amo con todo<br>
    mi corazón y quiero seguir construyendo<br>
    un mundo a tu lado. ❤️<br>
    <br>
    Siempre tuyo,<br>
    <b>Anth'Zz</b>
  </div>  <script>
    function mostrarTiempo() {
      document.getElementById("tiempo1").classList.add("hidden");
      document.getElementById("tiempo2").classList.remove("hidden");
    }

    const tiempo1 = "❤️ 1 año, 8 meses y 0 días juntos ❤️";
    document.getElementById("tiempo1").innerText = tiempo1;

    const tiempo2 = `💖 Hemos compartido:<br>
      🗓️ 608 días<br>
      ⏰ 14,592 horas<br>
      ⏱️ 875,520 minutos<br>
      💓 52,531,200 segundos de amor`;
    document.getElementById("tiempo2").innerHTML = tiempo2;
  </script></body>
</html>
