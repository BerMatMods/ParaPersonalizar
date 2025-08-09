<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Feliz Aniversario 💖</title>
<style>
/* ======== ESTILO GENERAL ======== */
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: linear-gradient(135deg, #4a148c, #880e4f);
  color: white;
  text-align: center;
  overflow-x: hidden;
}

/* ======== PANTALLA DE ACCESO ======== */
#pantallaClave {
  position: fixed;
  top: 0; left: 0;
  width: 100%; height: 100%;
  background: linear-gradient(135deg, #6a1b9a, #ad1457);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  z-index: 9999;
}

#pantallaClave h2 {
  font-size: 2em;
  margin-bottom: 20px;
  color: #ff80ab;
  text-shadow: 0 0 15px #ff4081;
}

.opcion-btn {
  background: linear-gradient(45deg, #d500f9, #ff4081);
  border: none;
  border-radius: 25px;
  padding: 15px 30px;
  margin: 10px;
  font-size: 1.2em;
  color: white;
  cursor: pointer;
  box-shadow: 0 0 20px #ff80ab;
  transition: transform 0.2s ease;
}
.opcion-btn:hover {
  transform: scale(1.1);
}

/* ======== CONTENIDO PRINCIPAL ======== */
#contenidoPrincipal {
  display: none;
  padding: 20px;
}

/* Contador con efecto de corazones */
.contador-box {
  position: relative;
  background: rgba(0,0,0,0.3);
  padding: 20px;
  border-radius: 15px;
  box-shadow: 0 0 20px #ff4081;
  margin: 20px auto;
  max-width: 600px;
  overflow: hidden;
}
#corazonesCanvas {
  position: absolute;
  top: 0; left: 0;
  width: 100%; height: 100%;
  pointer-events: none;
  z-index: 0;
}
#contador {
  position: relative;
  z-index: 1;
  font-size: 1.2em;
  color: #ff80ab;
}

/* ======== SECCIONES ======== */
section {
  margin: 40px 0;
}
img {
  max-width: 100%;
  border-radius: 10px;
  box-shadow: 0 0 20px #ff80ab;
}
</style>
</head>
<body>

<!-- ======== PANTALLA DE ACCESO ======== -->
<div id="pantallaClave">
  <h2>💖 ¿Qué tan goloza eres? 💖</h2>
  <button class="opcion-btn" onclick="verificar('Poco')">Poco</button>
  <button class="opcion-btn" onclick="verificar('Medio')">Medio</button>
  <button class="opcion-btn" onclick="verificar('Mucho')">Mucho</button>
</div>

<!-- ======== CONTENIDO PRINCIPAL ======== -->
<div id="contenidoPrincipal">
  <h1>💝 Feliz Aniversario Mi Amor 💝</h1>

  <!-- Contador -->
  <div class="contador-box">
    <canvas id="corazonesCanvas"></canvas>
    <div id="contador">Calculando...</div>
  </div>

  <!-- Aquí va tu contenido original -->
  <section>
    <h2>Nuestros Recuerdos</h2>
    <img src="imagen1.jpg" alt="Foto juntos">
  </section>
  <section>
    <h2>Momentos Especiales</h2>
    <img src="imagen2.jpg" alt="Momentos felices">
  </section>
  <button class="opcion-btn">TOCA AQUÍ MI REINA</button>
</div>

<script>
// ======== CONTROL DE ACCESO ========
function verificar(opcion) {
  if (opcion === "Mucho") {
    document.getElementById('pantallaClave').style.display = 'none';
    document.getElementById('contenidoPrincipal').style.display = 'block';
  } else {
    alert('Código incorrecto ❌');
  }
}

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

  contador.innerHTML = `💞 Llevamos: ${anos} años, ${meses} meses, ${dias} días, ${horas}h ${minutos}m ${segundos}s 💞`;
}
setInterval(actualizarContador, 1000);

// ======== CORAZONES CAYENDO ========
const canvas = document.getElementById('corazonesCanvas');
const ctx = canvas.getContext('2d');
let hearts = [];

function resizeCanvas() {
  canvas.width = canvas.offsetWidth;
  canvas.height = canvas.offsetHeight;
}
window.addEventListener('resize', resizeCanvas);
resizeCanvas();

function createHeart() {
  return {
    x: Math.random() * canvas.width,
    y: -20,
    size: Math.random() * 20 + 10,
    speed: Math.random() * 4 + 2, // rápido
    opacity: Math.random() * 0.5 + 0.5
  };
}

function drawHeart(h) {
  ctx.globalAlpha = h.opacity;
  ctx.fillStyle = "#ff80ab";
  ctx.beginPath();
  ctx.moveTo(h.x, h.y);
  ctx.bezierCurveTo(h.x - h.size / 2, h.y - h.size / 2, h.x - h.size, h.y + h.size / 3, h.x, h.y + h.size);
  ctx.bezierCurveTo(h.x + h.size, h.y + h.size / 3, h.x + h.size / 2, h.y - h.size / 2, h.x, h.y);
  ctx.fill();
  ctx.globalAlpha = 1;
}

function animateHearts() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  if (Math.random() < 0.3) { // más frecuencia
    hearts.push(createHeart());
  }
  hearts.forEach(h => {
    h.y += h.speed;
    drawHeart(h);
  });
  hearts = hearts.filter(h => h.y < canvas.height + 20);
  requestAnimationFrame(animateHearts);
}
animateHearts();
</script>

</body>
</html>
