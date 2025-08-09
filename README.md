<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Dedicatoria para Briyidth</title>
<link href="https://fonts.googleapis.com/css2?family=Dancing+Script&family=Great+Vibes&family=Raleway:wght@400;700&display=swap" rel="stylesheet" />
<style>
  body {
    background: linear-gradient(135deg, #0f0c29, #302b63, #24243e);
    font-family: 'Raleway', sans-serif;
    color: #f8bbd0;
    margin: 0; padding: 0;
    display: flex; flex-direction: column; align-items: center; min-height: 100vh;
    overflow-x: hidden;
  }

  .container {
    max-width: 720px;
    background: rgba(25, 0, 40, 0.85);
    margin: 60px 20px;
    padding: 30px 40px;
    border-radius: 25px;
    box-shadow: 0 0 30px #f48fb1;
    text-align: center;
    position: relative;
    z-index: 10;
  }

  .titulo {
    font-family: 'Dancing Script', cursive;
    font-size: 48px;
    color: #ff7eb9;
    text-shadow: 0 0 15px #ff79c6, 0 0 10px #f06292;
    margin-bottom: 15px;
  }

  .contador {
    font-size: 22px;
    font-weight: 700;
    margin: 15px 0 30px;
    color: #ff9ccf;
    letter-spacing: 1.2px;
    text-shadow: 0 0 12px #ff8ac1;
  }

  #reloj {
    font-family: 'Great Vibes', cursive;
    font-size: 30px;
    color: #ff6fae;
    margin-bottom: 40px;
    text-shadow: 0 0 15px #ff3b8a, 0 0 20px #ff6699;
  }

  #mensajeDedicatoria {
    font-family: 'Great Vibes', cursive;
    font-size: 28px;
    line-height: 1.5;
    color: #f48fb1;
    min-height: 120px;
    margin-bottom: 40px;
    text-shadow: 0 0 20px #ff6ea1;
    white-space: pre-wrap;
  }

  /* Corazones que caen */
  .corazon {
    position: fixed;
    top: -40px;
    color: #ff4da6;
    font-size: 18px;
    user-select: none;
    pointer-events: none;
    animation-name: caer;
    animation-timing-function: linear;
    animation-iteration-count: infinite;
  }

  @keyframes caer {
    0% {
      transform: translateY(0) rotate(0deg);
      opacity: 1;
    }
    100% {
      transform: translateY(110vh) rotate(360deg);
      opacity: 0;
    }
  }

  /* Máquina de escribir cursor */
  #cursor {
    display: inline-block;
    background-color: #ff69b4;
    width: 3px;
    animation: parpadear 1s infinite;
    margin-left: 3px;
    vertical-align: bottom;
  }
  @keyframes parpadear {
    0%, 50% { opacity: 1; }
    51%, 100% { opacity: 0; }
  }
</style>
</head>
<body>

<div class="container">
  <div class="titulo">💖 Para Mi Reina Briyidth 💖</div>
  <div class="contador" id="contador">Calculando el tiempo... ⏳</div>
  <div id="reloj">--:--:-- --</div>
  <div id="mensajeDedicatoria"></div>
</div>

<script>
  // Contador desde 10 Nov 2023
  const inicio = new Date("2023-11-10T00:00:00");
  const contadorEl = document.getElementById("contador");

  function actualizarContador() {
    const ahora = new Date();
    let anos = ahora.getFullYear() - inicio.getFullYear();
    let meses = ahora.getMonth() - inicio.getMonth();
    let dias = ahora.getDate() - inicio.getDate();
    let horas = ahora.getHours() - inicio.getHours();
    let minutos = ahora.getMinutes() - inicio.getMinutes();
    let segundos = ahora.getSeconds() - inicio.getSeconds();

    if (segundos < 0) { segundos += 60; minutos--; }
    if (minutos < 0) { minutos += 60; horas--; }
    if (horas < 0) { horas += 24; dias--; }
    if (dias < 0) {
      meses--;
      const mesAnterior = new Date(ahora.getFullYear(), ahora.getMonth(), 0);
      dias += mesAnterior.getDate();
    }
    if (meses < 0) { meses += 12; anos--; }

    contadorEl.textContent = `💞 YA VAMOS: ${anos} AÑOS, ${meses} MESES, ${dias} DÍAS, ${horas}h ${minutos}m ${segundos}s 💞`;
  }
  setInterval(actualizarContador, 1000);

  // Reloj en horario Perú (UTC-5) con AM/PM
  const relojEl = document.getElementById("reloj");

  function actualizarReloj() {
    const ahora = new Date();

    // Convertir a hora Perú (UTC-5)
    // Obtener hora UTC y restar 5 horas
    let utc = ahora.getTime() + (ahora.getTimezoneOffset() * 60000);
    let peruTime = new Date(utc - (5 * 3600000));

    let h = peruTime.getHours();
    let m = peruTime.getMinutes();
    let s = peruTime.getSeconds();
    let ampm = h >= 12 ? 'PM' : 'AM';

    h = h % 12;
    h = h ? h : 12; // 0 -> 12

    m = m < 10 ? '0'+m : m;
    s = s < 10 ? '0'+s : s;

    relojEl.textContent = `🕒 Hora Perú: ${h}:${m}:${s} ${ampm}`;
  }
  setInterval(actualizarReloj, 1000);
  actualizarReloj();

  // Mensajes de dedicatoria con máquina de escribir
  const mensajes = [
    "Mi Briyidth, cada día a tu lado es un regalo que nunca dejaré de agradecer.",
    "Tu sonrisa ilumina mis días más oscuros y llena mi alma de alegría.",
    "Eres la reina de mi corazón, mi inspiración y mi mejor amiga.",
    "Juntos hemos creado un mundo donde el amor siempre gana, sin importar nada más.",
    "Gracias por ser mi compañera, mi confidente y mi amor incondicional.",
    "Cada instante contigo es eterno, cada beso es un sueño hecho realidad.",
    "Prometo amarte y cuidarte en las buenas y en las malas, hoy y siempre.",
    "Te amo con toda mi alma, y nada ni nadie podrá cambiar eso, mi reina hermosa."
  ];

  const mensajeEl = document.getElementById("mensajeDedicatoria");
  const cursorEl = document.createElement('span');
  cursorEl.id = 'cursor';
  mensajeEl.appendChild(cursorEl);

  let i = 0; // índice de mensaje
  let charIndex = 0;
  let escribiendo = true;
  let timeoutId;

  function escribir() {
    if (charIndex <= mensajes[i].length && escribiendo) {
      mensajeEl.textContent = mensajes[i].substring(0, charIndex);
      mensajeEl.appendChild(cursorEl);
      charIndex++;
      timeoutId = setTimeout(escribir, 80);
    } else {
      escribiendo = false;
      timeoutId = setTimeout(borrar, 1800);
      if (i === 6 || i === 7) crearCorazones(); // más corazones en mensajes intensos
    }
  }

  function borrar() {
    if (charIndex >= 0 && !escribiendo) {
      mensajeEl.textContent = mensajes[i].substring(0, charIndex);
      mensajeEl.appendChild(cursorEl);
      charIndex--;
      timeoutId = setTimeout(borrar, 40);
    } else {
      escribiendo = true;
      i = (i + 1) % mensajes.length;
      timeoutId = setTimeout(escribir, 600);
    }
  }

  escribir();

  // Crear corazones animados que caen
  function crearCorazones() {
    for(let c=0; c<15; c++) {
      const heart = document.createElement('div');
      heart.classList.add('corazon');
      heart.style.left = Math.random() * window.innerWidth + 'px';
      heart.style.animationDuration = (3 + Math.random() * 2) + 's';
      heart.style.fontSize = (12 + Math.random() * 12) + 'px';
      heart.style.opacity = Math.random();
      heart.textContent = "❤️";
      document.body.appendChild(heart);

      // Remover corazón después de la animación
      setTimeout(() => heart.remove(), 5000);
    }
  }
</script>

</body>
</html>
