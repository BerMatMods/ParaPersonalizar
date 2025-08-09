<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<title>Contador Futurista Amoroso</title>
<style>
  body {
    margin: 0;
    font-family: 'Segoe UI', sans-serif;
    text-align: center;
    background: linear-gradient(135deg, #0d0221, #3a0ca3, #ff006e);
    background-size: 400% 400%;
    animation: fondoAnimado 10s ease infinite;
    color: #fff;
    font-size: 1.5em;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
  }
  @keyframes fondoAnimado {
    0% {background-position: 0% 50%;}
    50% {background-position: 100% 50%;}
    100% {background-position: 0% 50%;}
  }
  .contador-box {
    position: relative;
    background: rgba(0, 0, 0, 0.4);
    padding: 20px 40px;
    border-radius: 15px;
    box-shadow: 0 0 30px #ff4ecb;
    overflow: hidden;
  }
  #efectoCanvas {
    position: absolute;
    top: 0; left: 0;
    width: 100%; height: 100%;
    pointer-events: none;
    z-index: 0;
  }
  #contador, #reloj {
    position: relative;
    z-index: 1;
    text-shadow: 0 0 10px #ff4ecb, 0 0 20px #ff4ecb, 0 0 30px #ff4ecb;
  }
  #reloj {
    margin-top: 10px;
    font-size: 1.2em;
    color: #ffe4f5;
  }
</style>
</head>
<body>

<div class="contador-box">
  <canvas id="efectoCanvas"></canvas>
  <div id="contador">Calculando...</div>
  <div id="reloj">00:00:00</div>
</div>

<script>
// ======== CONTADOR ========
const inicio = new Date("2023-11-10T00:00:00");
const contador = document.getElementById("contador");

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

  contador.textContent = 
    `💖 Llevamos: ${anos} años, ${meses} meses, ${dias} días, ${horas}h ${minutos}m ${segundos}s 💖`;
}
setInterval(actualizarContador, 1000);
actualizarContador();

// ======== RELOJ DE PERÚ ========
const reloj = document.getElementById("reloj");
function actualizarReloj() {
  const ahora = new Date();
  const opciones = { timeZone: "America/Lima", hour12: false, hour: "2-digit", minute: "2-digit", second: "2-digit" };
  reloj.textContent = new Intl.DateTimeFormat("es-PE", opciones).format(ahora);
}
setInterval(actualizarReloj, 1000);
actualizarReloj();

// ======== EFECTO MATRIX DE CORAZONES Y ESTRELLAS ========
const canvas = document.getElementById('efectoCanvas');
const ctx = canvas.getContext('2d');
let elementos = [];

function resizeCanvas() {
  canvas.width = canvas.offsetWidth;
  canvas.height = canvas.offsetHeight;
}
window.addEventListener('resize', resizeCanvas);
resizeCanvas();

const simbolos = ["💖", "⭐", "💜", "✨", "❤️"];

function crearElemento() {
  return {
    x: Math.random() * canvas.width,
    y: -20,
    simbolo: simbolos[Math.floor(Math.random() * simbolos.length)],
    size: Math.random() * 20 + 15,
    speed: Math.random() * 3 + 2,
    opacity: Math.random() * 0.5 + 0.5
  };
}

function dibujarElemento(e) {
  ctx.globalAlpha = e.opacity;
  ctx.font = `${e.size}px Arial`;
  ctx.fillStyle = Math.random() > 0.5 ? "#ff80ab" : "#a770ff";
  ctx.fillText(e.simbolo, e.x, e.y);
  ctx.globalAlpha = 1;
}

function animarElementos() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  if (Math.random() < 0.4) {
    elementos.push(crearElemento());
  }
  elementos.forEach(el => {
    el.y += el.speed;
    dibujarElemento(el);
  });
  elementos = elementos.filter(el => el.y < canvas.height + 20);
  requestAnimationFrame(animarElementos);
}
animarElementos();
</script>

</body>
</html>
