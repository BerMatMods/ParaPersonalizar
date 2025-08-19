<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>BerMa_Mods 💖</title>
  <link href="https://fonts.googleapis.com/css2?family=Dancing+Script&family=Pacifico&family=Great+Vibes&family=Orbitron:wght@400;700&display=swap" rel="stylesheet">
  <style>
    /* Reset */
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      background: #000;
      color: #fff;
      font-family: 'Orbitron', sans-serif;
      display: flex;
      flex-direction: column;
      align-items: center;
      min-height: 100vh;
      overflow: hidden;
      position: relative;
    }

    /* --- FONDO DE ESTRELLAS (OPCIONAL) --- */
    body::before {
      content: '';
      position: fixed;
      top: 0; left: 0;
      width: 100%; height: 100%;
      background: radial-gradient(ellipse at center, transparent 60%, #000 100%), repeating-radial-gradient(ellipse at center, #0f0f20 1px, transparent 2px, transparent 10px);
      z-index: -1;
      pointer-events: none;
      opacity: 0.3;
    }

    /* --- PANTALLAS DE ACCESO (NEÓN) --- */
    .pantalla {
      position: fixed;
      top: 0; left: 0;
      width: 100%; height: 100%;
      background: rgba(0, 0, 0, 0.95);
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      z-index: 9999;
      padding: 20px;
      text-align: center;
      backdrop-filter: blur(4px);
      border: 2px solid #ff00ff;
      box-shadow: 0 0 30px #ff00ff, 0 0 60px rgba(255, 0, 255, 0.5);
    }

    .pantalla.hidden { display: none; }

    .pantalla h2 {
      font-family: 'Pacifico', cursive;
      font-size: 36px;
      color: #00ff00;
      text-shadow: 0 0 10px #00ff00, 0 0 20px #00ff00, 0 0 30px #00ff00;
      margin-bottom: 20px;
      animation: parpadeo-neon 1.5s infinite alternate;
    }

    /* --- INPUT DE CLAVE (NEÓN) --- */
    #claveInput {
      font-size: 28px;
      padding: 15px;
      border: 3px solid #00ffff;
      border-radius: 15px;
      text-align: center;
      width: 250px;
      margin-bottom: 20px;
      letter-spacing: 5px;
      color: #00ffff;
      background: rgba(0, 0, 0, 0.7);
      box-shadow: 0 0 20px #00ffff, inset 0 0 10px #00ffff;
      font-family: 'Orbitron', monospace;
    }

    /* --- TECLADO NEÓN --- */
    #teclado {
      display: grid;
      grid-template-columns: repeat(3, 80px);
      gap: 15px;
      margin-bottom: 20px;
    }

    .tecla {
      font-size: 24px;
      padding: 15px;
      background: rgba(0, 0, 0, 0.5);
      border: 2px solid #ff00ff;
      border-radius: 12px;
      color: #ff00ff;
      cursor: pointer;
      box-shadow: 0 0 15px #ff00ff, 0 5px 10px rgba(0, 0, 0, 0.5);
      user-select: none;
      transition: all 0.2s ease;
      font-family: 'Orbitron', sans-serif;
    }

    .tecla:hover {
      background: rgba(255, 0, 255, 0.2);
      transform: translateY(-3px);
      box-shadow: 0 0 25px #ff00ff, 0 10px 20px rgba(255, 0, 255, 0.3);
    }

    .tecla:active {
      transform: translateY(1px);
      box-shadow: 0 0 10px #ff00ff;
    }

    /* --- BOTÓN ACCEDER (NEÓN MORADO) --- */
    #accederBtn {
      padding: 15px 30px;
      font-size: 22px;
      background: rgba(0, 0, 0, 0.7);
      color: #ff00ff;
      border: 3px solid #ff00ff;
      border-radius: 30px;
      font-family: 'Pacifico', cursive;
      box-shadow: 0 0 25px #ff00ff, 0 0 50px rgba(255, 0, 255, 0.5);
      cursor: pointer;
      transition: all 0.3s ease;
      text-shadow: 0 0 10px #ff00ff;
    }

    #accederBtn:hover {
      background: rgba(255, 0, 255, 0.1);
      transform: scale(1.05);
      box-shadow: 0 0 40px #ff00ff, 0 0 70px rgba(255, 0, 255, 0.7);
    }

    /* --- STITCH EN NEÓN --- */
    #stitch {
      border: 4px solid #00ffff;
      border-radius: 20px;
      padding: 15px;
      background: rgba(0, 0, 0, 0.6);
      box-shadow: 0 0 25px #00ffff;
      margin-top: 20px;
      display: inline-block;
    }

    #stitch img {
      width: 200px;
      border-radius: 16px;
      border: 3px solid #00ff00;
      box-shadow: 0 0 20px #00ff00;
    }

    /* --- INFO DE SEGURIDAD (NEÓN VERDE) --- */
    #infoSeguridad {
      margin-top: 15px;
      color: #00ff00;
      font-family: 'Pacifico', cursive;
      font-size: 18px;
      text-shadow: 0 0 10px #00ff00;
    }

    /* --- PREGUNTA (NEÓN) --- */
    .pregunta-contenedor h2 {
      font-family: 'Pacifico', cursive;
      font-size: 32px;
      color: #00ffff;
      text-shadow: 0 0 10px #00ffff, 0 0 20px #00ffff;
      margin-bottom: 20px;
    }

    .opciones button {
      padding: 15px 20px;
      font-size: 18px;
      border-radius: 16px;
      background: rgba(0, 0, 0, 0.6);
      border: 2px solid #00ffff;
      color: #00ffff;
      cursor: pointer;
      box-shadow: 0 0 15px #00ffff;
      font-weight: 700;
      max-width: 340px;
      margin: 10px auto;
      transition: all 0.3s ease;
      font-family: 'Orbitron', sans-serif;
    }

    .opciones button:hover {
      transform: translateY(-4px);
      box-shadow: 0 0 25px #00ffff, 0 10px 20px rgba(0, 255, 255, 0.2);
    }

    .opciones button.correct {
      border-color: #ff00ff;
      color: #ff00ff;
      box-shadow: 0 0 25px #ff00ff;
    }

    /* --- MODAL DE ERROR (NEÓN ROJO) --- */
    #modalError {
      position: fixed;
      left: 50%;
      top: 15%;
      transform: translateX(-50%);
      min-width: 280px;
      max-width: 90%;
      background: rgba(0, 0, 0, 0.9);
      border: 3px solid #ff0000;
      border-radius: 20px;
      padding: 20px;
      box-shadow: 0 0 30px #ff0000, 0 0 60px rgba(255, 0, 0, 0.4);
      z-index: 10050;
      display: none;
      text-align: center;
      animation: popup 0.3s ease;
    }

    #modalError h3 {
      color: #ff0000;
      font-family: 'Pacifico', cursive;
      font-size: 22px;
      text-shadow: 0 0 10px #ff0000;
      margin: 8px 0;
    }

    #modalError p {
      color: #ff5555;
      font-weight: 700;
      margin: 10px 0;
    }

    #modalError button {
      padding: 10px 20px;
      border-radius: 14px;
      background: rgba(0, 0, 0, 0.7);
      border: 2px solid #ff0000;
      color: #ff0000;
      cursor: pointer;
      box-shadow: 0 0 15px #ff0000;
      font-weight: 700;
    }

    /* --- CONTENIDO PRINCIPAL --- */
    #contenidoPrincipal {
      display: none;
      width: 100%;
      padding: 40px 12px 80px;
      flex-direction: column;
      align-items: center;
    }

    .container {
      text-align: center;
      margin-top: 60px;
      padding: 40px;
      border-radius: 30px;
      background: rgba(0, 0, 0, 0.8);
      box-shadow: 0 0 40px #ff00ff, 0 0 80px rgba(255, 0, 255, 0.3);
      width: 90%;
      max-width: 700px;
      border: 3px solid #ff00ff;
    }

    .titulo {
      font-family: 'Dancing Script', cursive;
      font-size: 56px;
      color: #ff00ff;
      text-shadow: 0 0 15px #ff00ff, 0 0 30px #ff00ff, 0 0 50px #ff00ff;
      animation: pulso 2s infinite alternate;
      margin-bottom: 20px;
    }

    .contador {
      font-size: 22px;
      color: #00ffff;
      font-weight: 700;
      margin-top: 20px;
      text-shadow: 0 0 10px #00ffff;
    }

    .btn {
      margin: 35px auto 0;
      padding: 22px 45px;
      font-size: 26px;
      background: rgba(0, 0, 0, 0.7);
      border: 3px solid #00ff00;
      color: #00ff00;
      border-radius: 40px;
      cursor: pointer;
      box-shadow: 0 0 30px #00ff00, 0 0 60px rgba(0, 255, 0, 0.3);
      font-family: 'Pacifico', cursive;
      transition: all 0.3s ease;
      user-select: none;
      display: inline-block;
      text-shadow: 0 0 10px #00ff00;
    }

    .btn:hover {
      transform: scale(1.08);
      box-shadow: 0 0 40px #00ff00, 0 0 80px rgba(0, 255, 0, 0.5);
    }

    .mensaje {
      margin-top: 35px;
      padding: 35px;
      background: rgba(0, 0, 0, 0.7);
      border-radius: 25px;
      font-size: 24px;
      color: #00ffff;
      box-shadow: 0 0 30px #00ffff;
      font-family: 'Great Vibes', cursive;
      text-shadow: 0 0 10px #00ffff;
      display: none;
      border: 2px solid #00ffff;
    }

    .imagen-extra {
      margin-top: 30px;
      display: none;
    }

    .imagen-extra img {
      max-width: 90%;
      border-radius: 30px;
      box-shadow: 0 0 40px #ff00ff;
      border: 5px solid #ff00ff;
    }

    /* --- MUÑEQUITOS NEÓN (3 nuevos cuadros con diferentes colores) --- */
    .muñequitos {
      position: fixed;
      bottom: 10px;
      left: 0;
      width: 100%;
      text-align: center;
      padding: 15px 0;
      z-index: 10;
      display: flex;
      justify-content: center;
      gap: 30px;
    }

    .muñequitos .cuadro {
      display: inline-block;
      background: rgba(0, 0, 0, 0.6);
      border-radius: 25px;
      padding: 15px;
      box-shadow: 0 0 20px #00ffff;
      border: 3px solid #00ffff;
      animation: rebote 2.5s infinite ease-in-out;
    }

    .muñequitos .cuadro:nth-child(2) {
      box-shadow: 0 0 20px #ff00ff;
      border-color: #ff00ff;
    }

    .muñequitos .cuadro:nth-child(3) {
      box-shadow: 0 0 20px #00ff00;
      border-color: #00ff00;
    }

    .muñequitos img {
      width: 90px;
      height: 90px;
      border-radius: 15px;
      animation: muñequito-bailando 2.5s infinite;
    }

    /* --- GALERÍA NEÓN --- */
    #btnGaleria {
      margin-top: 25px;
      background: rgba(0, 0, 0, 0.7);
      border: 3px solid #00ffff;
      color: #00ffff;
      border-radius: 35px;
      padding: 18px 35px;
      font-size: 22px;
      font-family: 'Pacifico', cursive;
      cursor: pointer;
      box-shadow: 0 0 25px #00ffff;
      transition: all 0.3s ease;
      text-shadow: 0 0 10px #00ffff;
    }

    #btnGaleria:hover {
      transform: scale(1.1);
      box-shadow: 0 0 40px #00ffff, 0 0 70px rgba(0, 255, 255, 0.5);
    }

    #galeria {
      display: none;
      margin-top: 30px;
      max-width: 700px;
      text-align: center;
    }

    #galeria .cuadro-foto {
      display: inline-block;
      margin: 12px;
      border: 4px solid #ff00ff;
      border-radius: 20px;
      overflow: hidden;
      box-shadow: 0 0 20px #ff00ff;
      background: rgba(0, 0, 0, 0.5);
      transition: transform 0.3s ease, box-shadow 0.3s ease;
      cursor: pointer;
      width: 160px;
      height: 160px;
    }

    #galeria .cuadro-foto:hover {
      transform: scale(1.08);
      box-shadow: 0 0 30px #ff00ff, 0 0 60px rgba(255, 0, 255, 0.5);
    }

    #galeria img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    /* --- CURSOR NEÓN --- */
    .cursor {
      display: inline-block;
      width: 10px;
      height: 24px;
      background-color: #00ffff;
      margin-left: 5px;
      animation: parpadeo-neon 0.8s infinite;
      vertical-align: middle;
    }

    /* --- ANIMACIONES --- */
    @keyframes parpadeo-neon {
      0%, 100% { opacity: 1; }
      50% { opacity: 0.4; }
    }

    @keyframes pulso {
      0% { text-shadow: 0 0 15px #ff00ff; }
      100% { text-shadow: 0 0 30px #ff00ff, 0 0 60px #ff00ff; }
    }

    @keyframes rebote {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-15px); }
    }

    @keyframes muñequito-bailando {
      0% { transform: translateY(0); }
      50% { transform: translateY(-15px); }
      100% { transform: translateY(0); }
    }

    @keyframes popup {
      from { transform: translate(-50%, -10px); opacity: 0; }
      to { transform: translate(-50%, 0); opacity: 1; }
    }

    @keyframes aparecer {
      0% { opacity: 0; transform: translateY(30px); }
      100% { opacity: 1; transform: translateY(0); }
    }
  </style>
</head>
<body>
  <!-- PANTALLA 1: ingreso de clave -->
  <div id="pantallaClave" class="pantalla">
    <h2>🔒 Código para acceder</h2>
    <input type="text" id="claveInput" placeholder="10/11/23" maxlength="8" readonly>
    <div id="teclado"></div>
    <button id="accederBtn">Acceder</button>

    <div id="stitch">
      <img src="https://media0.giphy.com/media/v1.Y2lkPTZjMDliOTUydXRucTZibGt3cDRhdTA1NXQzOG04ejZ6NGVtbXNzMjAxemp3ZnZjOSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9cw/huXuyCODzzCQLy3T05/giphy.gif" alt="Stitch Amoroso">
    </div>

    <div id="infoSeguridad">
      By: <b>Anth'Zz Berrocal</b><br>👽  <strong>BerMat Proyects</strong> 👽
    </div>
  </div>

  <!-- PANTALLA 2: pregunta -->
  <div id="pantallaPregunta" class="pantalla hidden">
    <div class="pregunta-contenedor">
      <h2>❓ ¿Qué tan golosa eres…?</h2>
      <div class="opciones">
        <button data-resp="1">No soy Goloza</button>
        <button data-resp="2">Soy poco Goloza</button>
        <button data-resp="3" class="correct">Soy muy Goloza 🔥</button>
      </div>
    </div>
  </div>

  <!-- MODAL DE ERROR -->
  <div id="modalError" role="alert" aria-hidden="true">
    <h3>❌ Respuesta incorrecta</h3>
    <p>Estás mintiendo Mamaguevo... 😢💕</p>
    <button id="cerrarModal">Volver a intentar</button>
  </div>

  <!-- CONTENIDO PRINCIPAL -->
  <div id="contenidoPrincipal">
    <div class="container">
      <div class="titulo">💖 Feliz Aniversario Mi Amorcita hermosa 💖</div>
      <div class="contador" id="contador">Calculando el tiempo... ⏳</div>

      <button class="btn" id="btnSorpresa">TOCA AQUÍ MI REINA</button>

      <div class="mensaje" id="mensaje"></div>
      <span class="cursor" id="cursor"></span>

      <div class="imagen-extra" id="imagenExtra">
        <img src="https://i.postimg.cc/j5HdGJKJ/Screenshot-20250810-134752.jpg" alt="Foto de nosotros" />
      </div> 

      <button id="btnGaleria">Ver nuestra galería 📸</button>

      <div id="galeria">
        <div class="cuadro-foto"><img src="https://i.postimg.cc/HkxS5Yjs/1742316301125-2.jpg" alt=""></div>
        <div class="cuadro-foto"><img src="https://i.postimg.cc/8PkwQpRB/Screenshot-20250427-213138.jpg" alt=""></div>
        <div class="cuadro-foto"><img src="https://i.postimg.cc/VNsb5vND/received-1162848851410899.jpg" alt=""></div>
        <div class="cuadro-foto"><img src="https://i.postimg.cc/RVRShRnx/PSX-20250530-060357.jpg" alt=""></div>
        <div class="cuadro-foto"><img src="https://i.postimg.cc/59KpJcnh/IMG-20241228-231305-817-3.jpg" alt=""></div>
      </div>
    </div>

    <!-- MUÑEQUITOS NEÓN (3 cuadros de colores diferentes) -->
    <div class="muñequitos" aria-hidden="true">
      <div class="cuadro"><img src="https://media0.giphy.com/media/yN5xPFm8klwMddZVKi/giphy.gif" alt=""></div>
      <div class="cuadro"><img src="https://media2.giphy.com/media/5dkb3UXNiRU5qwNrzL/giphy.gif" alt=""></div>
      <div class="cuadro"><img src="https://media0.giphy.com/media/yN5xPFm8klwMddZVKi/giphy.gif" alt=""></div>
    </div>
  </div>

  <script>
    const input = document.getElementById('claveInput');
    const teclado = document.getElementById('teclado');
    const accederBtn = document.getElementById('accederBtn');
    const claveCorrecta = '10/11/23';

    const numeros = ['1','2','3','4','5','6','7','8','9','0','B','/'];
    numeros.forEach(n => {
      const tecla = document.createElement('div');
      tecla.className = 'tecla';
      tecla.textContent = n;
      tecla.onclick = () => {
        if (n === 'B') input.value = input.value.slice(0, -1);
        else if (input.value.length < 8) input.value += n;
      };
      teclado.appendChild(tecla);
    });

    accederBtn.addEventListener('click', () => {
      if (input.value === claveCorrecta) {
        document.getElementById('pantallaClave').classList.add('hidden');
        document.getElementById('pantallaPregunta').classList.remove('hidden');
      } else {
        alert('Código incorrecto ❌');
      }
    });

    const botonesPregunta = document.querySelectorAll('#pantallaPregunta .opciones button');
    const modalError = document.getElementById('modalError');
    const cerrarModal = document.getElementById('cerrarModal');

    botonesPregunta.forEach(btn => {
      btn.addEventListener('click', () => {
        const resp = btn.dataset.resp;
        if (resp === '3') {
          document.getElementById('pantallaPregunta').classList.add('hidden');
          document.getElementById('contenidoPrincipal').style.display = 'flex';
          iniciarTodo();
        } else {
          modalError.style.display = 'block';
          modalError.setAttribute('aria-hidden','false');
        }
      });
    });

    cerrarModal.addEventListener('click', () => {
      modalError.style.display = 'none';
      modalError.setAttribute('aria-hidden','true');
    });

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

      contador.innerHTML = `💞 𝐘𝐀 𝐕𝐀𝐌𝐎𝐒: ${anos} AÑOS, ${meses} MESES, ${dias} DÍAS, ${horas}h ${minutos}m ${segundos}s 💞`;
    }

    let intervaloContador = null;

    const btnSorpresa = document.getElementById("btnSorpresa");
    const mensaje = document.getElementById("mensaje");
    const imagenExtra = document.getElementById("imagenExtra");
    const btnGaleria = document.getElementById("btnGaleria");
    const galeria = document.getElementById("galeria");
    const cursor = document.getElementById("cursor");

    const texto = `🎉💖 ¡Feliz aniversario mi reina ! 💖🎉
Hoy celebramos otro mes más juntos, y mi corazón late más fuerte por ti cada día. 💕
Gracias por llegar a mi vida, por llenar mis días de risas, abrazos y momentos que nunca olvidaré. 🌹
Eres mi razón de sonreír, mi inspiración, mi fuerza y mi paz. 💌
Quiero que sepas que no importa lo que pase, siempre estaré a tu lado para cuidarte, apoyarte y amarte. 💍
Tu amor me ha hecho mejor persona, y no hay un solo segundo en el que no agradezca tenerte. ✨
Te prometo seguir luchando por nosotros, cumplir nuestros sueños y escribir juntos una historia que dure para siempre. 🌈
Cada beso tuyo me recuerda que el verdadero paraíso es tenerte cerca. 🌅
Eres mi todo, mi hogar, mi destino y mi vida entera. 💘
No hay distancia, tiempo o dificultad que pueda separarnos, porque nuestro amor es más fuerte que todo. 💞
Te amo con la intensidad de mil soles, con la ternura de mil lunas y con la eternidad de mil vidas. 🌠
💞 Mi reina hermosa, eres lo más valioso que tengo y siempre lo serás. 💞`;

    let i = 0;
    let escribirInterval = null;

    function iniciarEscritura() {
      mensaje.textContent = '';
      i = 0;
      mensaje.style.display = 'block';
      cursor.style.display = 'inline-block';
      escribirInterval = setInterval(() => {
        if (i < texto.length) {
          mensaje.textContent += texto.charAt(i);
          i++;
        } else {
          clearInterval(escribirInterval);
          cursor.style.display = 'none';
        }
      }, 45);
    }

    btnSorpresa.addEventListener('click', () => {
      iniciarEscritura();
      imagenExtra.style.display = 'block';
      btnSorpresa.disabled = true;
      btnSorpresa.style.cursor = 'not-allowed';
    });

    btnGaleria.addEventListener('click', () => {
      if (galeria.style.display === 'none' || galeria.style.display === '') {
        galeria.style.display = 'block';
        btnGaleria.textContent = "Ocultar galería 📸";
      } else {
        galeria.style.display = 'none';
        btnGaleria.textContent = "Ver nuestra galería 📸";
      }
    });

    function iniciarTodo() {
      if (intervaloContador) clearInterval(intervaloContador);
      actualizarContador();
      intervaloContador = setInterval(actualizarContador, 1000);
      cursor.style.display = 'none';
    }
  </script>
</body>
</html>
