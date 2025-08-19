<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>BerMa_Mods</title>
  <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Pacifico&family=Great+Vibes&family=Raleway:wght@400;700&display=swap" rel="stylesheet">
  <style>
    /* Reset */
    * { box-sizing: border-box; margin: 0; padding: 0; }

    /* FONDO OSCURO PARA RESALTAR EL NEÓN */
    body {
      margin: 0;
      background: #000;
      color: #fff;
      font-family: 'Raleway', sans-serif;
      display: flex;
      flex-direction: column;
      align-items: center;
      position: relative;
      min-height: 100vh;
      overflow: hidden;
      -webkit-font-smoothing: antialiased;
    }

    /* ---- PANTALLA DE ACCESO ---- */
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
      border: 2px solid #ff00ff;
      box-shadow: 0 0 30px rgba(255, 0, 255, 0.5);
    }
    .pantalla.hidden { display: none; }

    /* TÍTULO NEÓN ROSA */
    .pantalla h2 {
      font-size: 34px;
      color: #ff00ff;
      font-family: 'Pacifico', cursive;
      margin-bottom: 16px;
      text-shadow: 0 0 10px #ff00ff, 0 0 20px #ff00ff, 0 0 30px #ff00ff;
      animation: parpadeo 1.5s infinite alternate;
    }
    @keyframes parpadeo {
      from { opacity: 0.8; }
      to { opacity: 1; }
    }

    /* INPUT NEÓN */
    #claveInput {
      font-size: 26px;
      padding: 14px 18px;
      border: 3px solid #ff00ff;
      border-radius: 15px;
      text-align: center;
      width: 240px;
      margin-bottom: 16px;
      letter-spacing: 5px;
      color: #ff80ff;
      background: rgba(20, 0, 40, 0.6);
      box-shadow: 0 0 20px rgba(255, 0, 255, 0.4);
    }

    /* TECLADO NEÓN */
    #teclado {
      display: grid;
      grid-template-columns: repeat(3, 80px);
      gap: 14px;
      margin-bottom: 18px;
    }

    .tecla {
      font-size: 24px;
      padding: 14px;
      background: #330066;
      border: 2px solid #ff00ff;
      border-radius: 14px;
      color: #ff80ff;
      cursor: pointer;
      box-shadow: 0 0 15px rgba(255, 0, 255, 0.3);
      user-select: none;
    }
    .tecla:active {
      transform: translateY(3px);
      box-shadow: 0 0 20px rgba(0, 255, 255, 0.5);
    }

    /* BOTÓN NEÓN */
    #accederBtn {
      padding: 14px 30px;
      font-size: 22px;
      background: #990099;
      color: white;
      border: none;
      border-radius: 35px;
      font-family: 'Pacifico', cursive;
      box-shadow: 0 0 25px rgba(255, 0, 255, 0.6);
      cursor: pointer;
    }

    /* STITCH CON MARCO NEÓN */
    #stitch {
      border: 4px solid #ff00ff;
      border-radius: 20px;
      padding: 10px;
      box-shadow: 0 0 30px rgba(255, 0, 255, 0.6);
      margin-top: 20px;
      display: inline-block;
    }
    #stitch img {
      width: 190px;
      border-radius: 16px;
      border: 3px solid #fff;
    }

    /* INFO DE SEGURIDAD NEÓN */
    #infoSeguridad {
      margin-top: 18px;
      color: #ff00ff;
      font-family: 'Pacifico', cursive;
      font-size: 18px;
      text-shadow: 0 0 10px #ff00ff;
    }

    /* ---- CONTENIDO PRINCIPAL ---- */
    #contenidoPrincipal {
      display: none;
      width: 100%;
      padding: 50px 12px 190px;
      justify-content: center;
    }

    /* CONTENEDOR CON BORDE NEÓN DOBLE */
    .container {
      text-align: center;
      margin-top: 60px;
      padding: 40px;
      border-radius: 30px;
      background: rgba(30, 0, 60, 0.7);
      width: 90%;
      max-width: 720px;
      position: relative;
      border: 3px solid #ff00ff;
      box-shadow: 
        0 0 30px rgba(255, 0, 255, 0.5),
        0 0 50px rgba(255, 0, 255, 0.3) inset;
    }

    /* BORDE EXTERNO NEÓN ANIMADO */
    .container::before {
      content: '';
      position: absolute;
      inset: -5px;
      border-radius: 35px;
      border: 3px solid #00ffff;
      animation: rotar 4s linear infinite;
      box-shadow: 0 0 40px rgba(0, 255, 255, 0.4);
      z-index: -1;
    }
    .container::after {
      content: '';
      position: absolute;
      inset: -10px;
      border-radius: 40px;
      border: 3px solid #ffff00;
      animation: rotar 6s linear reverse infinite;
      box-shadow: 0 0 60px rgba(255, 255, 0, 0.3);
      z-index: -1;
      opacity: 0.6;
    }
    @keyframes rotar {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }

    /* TÍTULO NEÓN */
    .titulo {
      font-family: 'Dancing Script', cursive;
      font-size: 56px;
      color: #ff00ff;
      text-shadow: 0 0 20px #ff00ff, 0 0 30px #ff00ff;
    }

    /* CONTADOR NEÓN */
    .contador {
      font-size: 22px;
      color: #00ffff;
      font-weight: 700;
      margin-top: 25px;
      text-shadow: 0 0 10px #00ffff;
    }

    /* BOTÓN SORPRESA NEÓN */
    .btn {
      margin: 35px auto 0;
      padding: 22px 45px;
      font-size: 26px;
      background: #990099;
      border: 3px solid #ff00ff;
      color: white;
      border-radius: 40px;
      cursor: pointer;
      box-shadow: 0 0 30px rgba(255, 0, 255, 0.5);
      font-family: 'Pacifico', cursive;
      position: relative;
      z-index: 2;
    }

    /* MENSAJE NEÓN - TEXTO MEJORADO */
    .mensaje {
      margin-top: 35px;
      padding: 35px 30px;
      background: rgba(50, 0, 100, 0.4);
      border: 3px solid #ff00ff;
      border-radius: 25px;
      font-size: 26px;
      color: #fff;
      box-shadow: 0 0 35px rgba(255, 0, 255, 0.4);
      font-family: 'Great Vibes', cursive;
      text-shadow: 0 0 15px rgba(255, 0, 255, 0.7);
      display: none;
      position: relative;
      line-height: 1.6;
    }
    .mensaje::before {
      content: '';
      position: absolute;
      inset: -5px;
      border-radius: 30px;
      border: 3px solid #00ffff;
      animation: pulso 2s infinite alternate;
      box-shadow: 0 0 40px rgba(0, 255, 255, 0.4);
      z-index: -1;
    }
    @keyframes pulso {
      0% { opacity: 0.6; }
      100% { opacity: 1; }
    }

    /* FOTO EXTRA CON MARCO NEÓN */
    .imagen-extra {
      margin-top: 30px;
      display: none;
    }
    .imagen-extra img {
      max-width: 95%;
      border-radius: 30px;
      border: 5px solid #ff00ff;
      box-shadow: 0 0 40px rgba(255, 0, 255, 0.6);
    }
    .imagen-extra img::before {
      content: '';
      position: absolute;
      inset: -8px;
      border-radius: 38px;
      border: 3px solid #00ffff;
      animation: pulso 2.5s infinite alternate;
      box-shadow: 0 0 50px rgba(0, 255, 255, 0.5);
      z-index: -1;
    }

    /* GALERÍA NEÓN */
    #btnGaleria {
      margin-top: 25px;
      padding: 18px 35px;
      background: #990099;
      border: 3px solid #ff00ff;
      color: white;
      border-radius: 35px;
      font-size: 22px;
      font-family: 'Pacifico', cursive;
      cursor: pointer;
      box-shadow: 0 0 25px rgba(255, 0, 255, 0.5);
    }
    #galeria {
      display: none;
      margin-top: 30px;
      max-width: 720px;
      text-align: center;
    }
    #galeria .cuadro-foto {
      display: inline-block;
      margin: 12px;
      border: 3px solid #ff00ff;
      border-radius: 18px;
      overflow: hidden;
      width: 150px;
      height: 150px;
      position: relative;
      box-shadow: 0 0 20px rgba(255, 0, 255, 0.4);
    }
    #galeria .cuadro-foto::before {
      content: '';
      position: absolute;
      inset: -3px;
      border-radius: 21px;
      border: 2px solid #00ffff;
      animation: rotar 5s linear infinite;
      box-shadow: 0 0 30px rgba(0, 255, 255, 0.4);
      z-index: -1;
    }
    #galeria img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    /* VIDEO NEÓN */
    .video-container {
      position: fixed;
      bottom: 20px;
      left: 50%;
      transform: translateX(-50%);
      width: 90%;
      max-width: 640px;
      border: 4px solid #ff00ff;
      border-radius: 20px;
      overflow: hidden;
      box-shadow: 0 0 40px rgba(255, 0, 255, 0.6);
      z-index: 1000;
      position: relative;
    }
    .video-container::before {
      content: '';
      position: absolute;
      inset: -5px;
      border-radius: 25px;
      border: 3px solid #00ffff;
      animation: rotar 4s linear infinite;
      box-shadow: 0 0 50px rgba(0, 255, 255, 0.4);
      z-index: -1;
    }
    .video-container::after {
      content: '';
      position: absolute;
      inset: -10px;
      border-radius: 30px;
      border: 3px solid #ffff00;
      animation: rotar 7s linear reverse infinite;
      box-shadow: 0 0 70px rgba(255, 255, 0, 0.3);
      z-index: -1;
      opacity: 0.6;
    }
    .video-container iframe {
      width: 100%;
      height: 315px;
      border: none;
    }

    /* Muñequitos */
    .muñequitos {
      position: fixed;
      bottom: 170px;
      left: 0;
      width: 100%;
      text-align: center;
      z-index: 1;
    }
    .muñequitos .cuadro {
      display: inline-block;
      background: transparent;
      border: 3px solid #ff00ff;
      border-radius: 20px;
      padding: 15px;
      margin: 0 15px;
      box-shadow: 0 0 20px rgba(255, 0, 255, 0.5);
    }
    .muñequitos img {
      width: 85px;
      height: 85px;
      border-radius: 12px;
    }

    /* Cursor neón */
    .cursor {
      display: inline-block;
      width: 10px;
      height: 28px;
      background-color: #ff00ff;
      margin-left: 5px;
      animation: blink 0.8s infinite;
      border-radius: 2px;
    }
    @keyframes blink {
      0%,50%{opacity:1}
      51%,100%{opacity:0}
    }
  </style>
</head>
<body>

  <!-- PANTALLA DE ACCESO -->
  <div id="pantallaClave" class="pantalla">
    <h2>🔒 Código para acceder</h2>
    <input type="text" id="claveInput" placeholder="10/11/23" maxlength="8" readonly>
    <div id="teclado"></div>
    <button id="accederBtn">Acceder</button>

    <div id="stitch">
      <img src="https://media0.giphy.com/media/v1.Y2lkPTZjMDliOTUydXRucTZibGt3cDRhdTA1NXQzOG04ejZ6NGVtbXNzMjAxemp3ZnZjOSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9cw/huXuyCODzzCQLy3T05/giphy.gif" alt="Stitch Amoroso">
    </div>

    <div id="infoSeguridad">
      By: <b>AnthZz Berrocal</b><br>👽  <strong>BerMat Proyects</strong> 👽
    </div>
  </div>

  <!-- CONTENIDO PRINCIPAL -->
  <div id="contenidoPrincipal">
    <div class="container">
      <div class="titulo">💖 Mi Amor, Eres Mi Universo 💖</div>
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

    <div class="muñequitos">
      <div class="cuadro"><img src="https://media0.giphy.com/media/yN5xPFm8klwMddZVKi/giphy.gif" alt=""></div>
      <div class="cuadro"><img src="https://media2.giphy.com/media/5dkb3UXNiRU5qwNrzL/giphy.gif" alt=""></div>
      <div class="cuadro"><img src="https://media0.giphy.com/media/yN5xPFm8klwMddZVKi/giphy.gif" alt=""></div>
    </div>
  </div>

  <!-- VIDEO DE "LA BODA" DE COSCULLUELA -->
  <div class="video-container" id="videoContainer" style="display: none;">
    <iframe 
      id="videoIframe"
      src="" 
      title="La Boda - Cosculluela"
      frameborder="0" 
      allow="autoplay; encrypted-media; picture-in-picture" 
      allowfullscreen>
    </iframe>
  </div>

  <script>
    // --- TECLADO Y ACCESO ---
    const input = document.getElementById('claveInput');
    const teclado = document.getElementById('teclado');
    const accederBtn = document.getElementById('accederBtn');

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
      if (input.value === '10/11/23') {
        document.getElementById('pantallaClave').classList.add('hidden');
        setTimeout(() => {
          document.getElementById('contenidoPrincipal').style.display = 'flex';
        }, 300);
        iniciarTodo();
      } else {
        alert('Código incorrecto ❌');
      }
    });

    // --- CONTADOR ---
    const inicio = new Date("2023-11-10T00:00:00");
    const contador = document.getElementById("contador");
    let intervaloContador = null;

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

      contador.innerHTML = `✨ YA VAMOS: ${anos} AÑOS, ${meses} MESES, ${días} DÍAS ✨`;
    }

    // --- MENSAJE MEJORADO (más bonito y romántico) ---
    const mensaje = document.getElementById("mensaje");
    const cursor = document.getElementById("cursor");
    const btnSorpresa = document.getElementById("btnSorpresa");
    const imagenExtra = document.getElementById("imagenExtra");

    const textoBonito = `💫 Mi vida, mi amor, mi todo... Briyidth 💫
Cada segundo contigo es un regalo que mi corazón atesora.
Desde que llegaste, mi mundo cambió: ahora brilla, ahora late, ahora tiene sentido.
Eres la luz que ilumina mis días, el abrazo que calma mis noches, el sueño que nunca quiero despertar.
No hay palabra que pueda describir lo que siento, pero si pudiera, sería: eterno, infinito, verdadero.
Gracias por ser mi compañera, mi confidente, mi risa, mi paz.
Prometo amarte hoy, mañana y en todas las vidas que vengan.
Porque tú no eres solo mi amor… eres mi destino. 💖`;

    function iniciarEscritura() {
      mensaje.textContent = '';
      let i = 0;
      cursor.style.display = 'inline-block';
      mensaje.style.display = 'block';
      const intervalo = setInterval(() => {
        if (i < textoBonito.length) {
          mensaje.textContent += textoBonito[i];
          i++;
        } else {
          clearInterval(intervalo);
          cursor.style.display = 'none';
        }
      }, 45);
    }

    btnSorpresa.addEventListener('click', () => {
      iniciarEscritura();
      imagenExtra.style.display = 'block';
      btnSorpresa.disabled = true;
    });

    // --- GALERÍA ---
    const btnGaleria = document.getElementById("btnGaleria");
    const galeria = document.getElementById("galeria");

    btnGaleria.addEventListener('click', () => {
      galeria.style.display = galeria.style.display === 'block' ? 'none' : 'block';
      btnGaleria.textContent = galeria.style.display === 'block' ? "❌ Ocultar galería" : "✨ Ver nuestra galería";
    });

    // --- VIDEO ---
    const videoContainer = document.getElementById('videoContainer');
    const videoIframe = document.getElementById('videoIframe');

    document.body.addEventListener('click', function activarVideo() {
      if (!videoContainer.style.display || videoContainer.style.display === 'none') {
        videoContainer.style.display = 'block';
        videoIframe.src = 'https://www.youtube.com/embed/K9L0JGpXg6A?autoplay=1&controls=1&showinfo=0&rel=0';
      }
      document.body.removeEventListener('click', activarVideo);
    }, { once: false });

    // --- INICIAR TODO ---
    function iniciarTodo() {
      actualizarContador();
      intervaloContador = setInterval(actualizarContador, 1000);
    }
  </script>
</body>
</html>
