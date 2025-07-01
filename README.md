<!DOCTYPE html><html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Feliz Aniversario Mi Reina</title>
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', sans-serif;
      background: linear-gradient(to top right, #ffe4ec, #ffd6f0);
      overflow: hidden;
      text-align: center;
      color: #880e4f;
    }h1 {
  font-size: 2.5em;
  margin-top: 40px;
  animation: fadeIn 2s ease-in-out;
}

#contador {
  font-size: 1.5em;
  margin: 20px 0;
  font-weight: bold;
  animation: fadeIn 2.5s ease-in-out;
}

.boton {
  padding: 15px 30px;
  background-color: #ec407a;
  color: white;
  border: none;
  border-radius: 50px;
  font-size: 1.2em;
  cursor: pointer;
  transition: background 0.3s ease;
  animation: fadeIn 3s ease-in-out;
}

.boton:hover {
  background-color: #d81b60;
}

#carta {
  display: none;
  max-width: 80%;
  margin: 30px auto;
  font-size: 1.2em;
  background: white;
  padding: 20px;
  border-radius: 15px;
  box-shadow: 0 0 10px #c2185b;
  animation: fadeIn 2s ease-in-out forwards;
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

.corazones {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  z-index: -1;
}

.corazon {
  position: absolute;
  width: 20px;
  height: 20px;
  background: red;
  transform: rotate(45deg);
  animation: flotar 10s linear infinite;
}

.corazon::before, .corazon::after {
  content: '';
  position: absolute;
  width: 20px;
  height: 20px;
  background: red;
  border-radius: 50%;
}

.corazon::before {
  top: -10px;
  left: 0;
}
.corazon::after {
  left: -10px;
  top: 0;
}

@keyframes flotar {
  0% { transform: translateY(100vh) rotate(45deg); }
  100% { transform: translateY(-10vh) rotate(45deg); }
}

  </style>
</head>
<body>
  <div class="corazones">
    <!-- Corazones aleatorios -->
    <script>
      for (let i = 0; i < 30; i++) {
        const heart = document.createElement('div');
        heart.classList.add('corazon');
        heart.style.left = Math.random() * 100 + 'vw';
        heart.style.animationDuration = (5 + Math.random() * 5) + 's';
        heart.style.opacity = Math.random();
        document.body.appendChild(heart);
      }
    </script>
  </div>  <h1>💖 FELIZ ANIVERSARIO MI REINA 💖</h1>
  <div id="contador">Calculando el tiempo que estamos juntos...</div><button class="boton" onclick="mostrarCarta()">💌 Haz click aquí mi mami</button>

  <div id="carta">
    <p>Te amo mucho mi amor, mi reina hermosa. 💘<br>
    Gracias por llegar a mi vida, eres lo más valioso que tengo y tengo miedo a perderte.<br>
    Siempre te voy a amar en las buenas y en las malas y sé que juntos vamos a salir adelante.<br>
    <strong>Te amo muchísimo mi mami ❤️</strong></p>
  </div>  <script>
    const fechaInicio = new Date("2023-11-10T00:00:00");
    const fechaFinal = new Date("2025-07-10T00:00:00");

    function actualizarContador() {
      const ahora = fechaFinal;
      const diff = ahora - fechaInicio;

      const segundosTotales = Math.floor(diff / 1000);
      const minutosTotales = Math.floor(segundosTotales / 60);
      const horasTotales = Math.floor(minutosTotales / 60);
      const diasTotales = Math.floor(horasTotales / 24);

      const años = Math.floor(diasTotales / 365);
      const meses = Math.floor((diasTotales % 365) / 30);
      const dias = (diasTotales % 365) % 30;

      document.getElementById("contador").innerHTML =
        `🕰️ ${años} años, ${meses} meses y ${dias} días juntos ❤️<br>` +
        `📆 Total: ${diasTotales} días, ${horasTotales} horas, ${minutosTotales} minutos y ${segundosTotales} segundos contigo mi amor.`;
    }

    function mostrarCarta() {
      document.getElementById("carta").style.display = 'block';
    }

    actualizarContador();
  </script></body>
</html>
