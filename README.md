<!DOCTYPE html><html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Feliz Aniversario Mi Reina</title>
  <link href="https://fonts.googleapis.com/css2?family=Pacifico&family=Orbitron&family=Courgette&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      font-family: 'Courgette', cursive;
      background: radial-gradient(circle, #ffe4ec, #ffc1e3);
      overflow: hidden;
      text-align: center;
      color: #880e4f;
    }h1 {
  font-size: 3em;
  margin-top: 40px;
  animation: fadeIn 2s ease-in-out;
}

#contador {
  font-family: 'Orbitron', sans-serif;
  font-size: 1.7em;
  margin: 20px auto;
  font-weight: bold;
  padding: 15px;
  width: 80%;
  background: #fff5f9;
  border-radius: 15px;
  box-shadow: 0 0 15px #ec407a;
  animation: fadeIn 2.5s ease-in-out;
}

.boton {
  padding: 15px 30px;
  background-color: #ec407a;
  color: white;
  border: none;
  border-radius: 50px;
  font-size: 1.3em;
  cursor: pointer;
  transition: background 0.3s ease;
  animation: fadeIn 3s ease-in-out;
  font-family: 'Orbitron', sans-serif;
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

#mensaje-final {
  display: none;
  font-size: 2.3em;
  margin-top: 30px;
  animation: explotar 1s ease-in-out forwards;
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes explotar {
  0% { transform: scale(0.5); opacity: 0; }
  100% { transform: scale(1.4); opacity: 1; color: #d50000; }
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

#by {
  font-size: 0.9em;
  margin-top: 50px;
  color: #880e4f;
}

  </style>
</head>
<body>
  <div class="corazones">
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
  </div>  <div id="mensaje-final">💣 VAMOS POR MÁS MI AMOR 💣</div>
  <div id="by">By Anth'Zz Berrocal</div>  <script>
    const inicio = new Date("2023-11-10T00:00:00");
    const fin = new Date("2025-07-10T00:00:00");

    function calcularTiempoExacto() {
      let años = fin.getFullYear() - inicio.getFullYear();
      let meses = fin.getMonth() - inicio.getMonth();
      let dias = fin.getDate() - inicio.getDate();

      if (dias < 0) {
        meses -= 1;
        dias += new Date(fin.getFullYear(), fin.getMonth(), 0).getDate();
      }
      if (meses < 0) {
        años -= 1;
        meses += 12;
      }
      return { años, meses, dias };
    }

    function actualizarContador() {
      const total = fin - inicio;
      const segundosTotales = Math.floor(total / 1000);

      const exacto = calcularTiempoExacto();
      let texto = `🕰️ ${exacto.años} años, ${exacto.meses} meses y ${exacto.dias} días juntos ❤️<br>`;

      let i = 0;
      const velocidad = 30; // más rápido aún

      const interval = setInterval(() => {
        if (i <= segundosTotales) {
          let seg = i;
          let min = Math.floor(seg / 60);
          let hrs = Math.floor(min / 60);
          let dias = Math.floor(hrs / 24);
          document.getElementById("contador").innerHTML = texto +
            `📆 Total: <strong>${dias}</strong> días, <strong>${hrs}</strong> horas, <strong>${min}</strong> minutos y <strong>${seg}</strong> segundos contigo mi amor.`;
          i += velocidad;
        } else {
          clearInterval(interval);
          document.getElementById("mensaje-final").style.display = 'block';
        }
      }, 15);
    }

    function mostrarCarta() {
      document.getElementById("carta").style.display = 'block';
    }

    actualizarContador();
  </script></body>
</html>
