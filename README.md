
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no" />
  <title>Detalles Virtuales - Crea tu Carta de Amor</title>

  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Playfair+Display:wght@700&family=Poppins:wght@400;500&display=swap" rel="stylesheet">

  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(135deg, #fff8fd, #fdf2f8, #fce5f0);
      color: #444;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      padding: 20px;
      overflow-x: hidden;
      position: relative;
    }

    /* Animación de borde brillante RGB */
    @keyframes rainbowGlow {
      0% { box-shadow: 0 0 15px rgba(255, 105, 180, 0.6); }
      25% { box-shadow: 0 0 15px rgba(140, 100, 255, 0.6); }
      50% { box-shadow: 0 0 15px rgba(0, 200, 255, 0.6); }
      75% { box-shadow: 0 0 15px rgba(255, 190, 100, 0.6); }
      100% { box-shadow: 0 0 15px rgba(255, 105, 180, 0.6); }
    }

    .glow-frame {
      position: relative;
      display: inline-block;
      border-radius: 20px;
      margin: 1rem 0;
      animation: rainbowGlow 3s ease-in-out infinite alternate;
      background: linear-gradient(45deg, #ff80ab, #ba68c8, #4fc3f7, #ffcc80);
      padding: 4px;
    }

    .glow-frame img {
      border-radius: 18px;
      display: block;
      width: 100%;
      height: auto;
      border: 4px solid #fff;
      filter: brightness(1) blur(0.5px);
      transition: transform 0.3s ease;
    }

    .glow-frame img:hover {
      transform: scale(1.03);
    }

    /* Pantalla de creación */
    .create-screen {
      text-align: center;
      padding: 1.8rem 2rem;
      max-width: 460px;
      background: rgba(255, 255, 255, 0.98);
      border-radius: 32px;
      box-shadow: 0 16px 45px rgba(255, 105, 180, 0.25);
      border: 3px solid transparent;
      background-clip: padding-box;
      position: relative;
      z-index: 1;
      margin-bottom: 30px;
    }

    .create-screen h2 {
      font-family: 'Playfair Display', serif;
      font-size: 2.1rem;
      background: linear-gradient(45deg, #e91e63, #ba68c8, #ff8f00);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      margin: 1rem 0;
    }

    .form-group {
      margin: 1.2rem 0;
    }

    label {
      display: block;
      text-align: left;
      margin-bottom: 8px;
      color: #d81b60;
      font-weight: 600;
    }

    input, textarea, select {
      width: 100%;
      padding: 10px 12px;
      border: 2px solid #ff80ab;
      border-radius: 14px;
      font-size: 1em;
      background: #fff9fb;
      color: #555;
      font-family: inherit;
    }

    textarea {
      resize: vertical;
      min-height: 100px;
    }

    button {
      margin: 1.3rem auto;
      padding: 0.9rem 2rem;
      font-size: 1.25rem;
      font-weight: 600;
      background: linear-gradient(45deg, #e91e63, #ba68c8);
      color: white;
      border: none;
      border-radius: 32px;
      cursor: pointer;
      box-shadow: 0 8px 20px rgba(233, 30, 99, 0.4);
      transition: all 0.3s ease;
      display: block;
    }

    button:hover {
      transform: scale(1.08);
      box-shadow: 0 10px 25px rgba(233, 30, 99, 0.5);
    }

    /* Pantalla de bloqueo */
    .lock-screen {
      display: none;
      text-align: center;
      padding: 1.8rem 2rem;
      max-width: 440px;
      background: rgba(255, 255, 255, 0.98);
      border-radius: 32px;
      box-shadow: 0 16px 45px rgba(255, 105, 180, 0.25);
      border: 3px solid transparent;
      background-clip: padding-box;
      position: relative;
      z-index: 1;
    }

    .lock-screen::before {
      content: '';
      position: absolute;
      inset: -3px;
      background: linear-gradient(45deg, #ff80ab, #ba68c8, #ffcc80);
      border-radius: 35px;
      z-index: -1;
      opacity: 0.7;
      animation: backgroundShift 6s ease-in-out infinite;
    }

    @keyframes backgroundShift {
      0%, 100% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
    }

    .lock-screen h2 {
      font-family: 'Playfair Display', serif;
      font-size: 2.1rem;
      background: linear-gradient(45deg, #e91e63, #ba68c8, #ff8f00);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      margin: 1rem 0;
      animation: backgroundShift 6s ease-in-out infinite;
    }

    .lock-screen p {
      color: #d81b60;
      font-size: 1.15rem;
      margin-bottom: 1.3rem;
      font-weight: 500;
    }

    .key-display {
      font-family: 'Poppins', monospace;
      font-size: 1.8rem;
      color: #e91e63;
      background: linear-gradient(135deg, #fff0f5, #ffe6f0);
      padding: 0.9rem 1.3rem;
      border-radius: 16px;
      margin: 1.1rem auto;
      width: 90%;
      border: 3px solid #ff80ab;
      letter-spacing: 4px;
      box-shadow: 0 6px 15px rgba(255, 105, 180, 0.2);
    }

    .keypad {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 12px;
      margin: 1.3rem 0;
    }

    .key {
      font-size: 1.45rem;
      font-weight: 600;
      padding: 1rem 0;
      background: linear-gradient(135deg, #fff5f8, #ffe6f0);
      color: #e91e63;
      border: 3px solid #ff80ab;
      border-radius: 14px;
      cursor: pointer;
      transition: all 0.25s cubic-bezier(0.25, 0.8, 0.25, 1);
      box-shadow: 0 4px 10px rgba(255, 105, 180, 0.2);
    }

    .key:hover {
      background: linear-gradient(135deg, #ffe6f0, #f8dafa);
      transform: translateY(-4px);
      box-shadow: 0 8px 18px rgba(255, 105, 180, 0.35);
    }

    .key:active {
      transform: scale(0.95);
      box-shadow: 0 3px 8px rgba(233, 30, 99, 0.3);
    }

    .btn-iniciar {
      margin-top: 1.4rem;
      padding: 0.9rem 2rem;
      font-size: 1.25rem;
      font-weight: 600;
      background: linear-gradient(45deg, #e91e63, #ba68c8, #8e24aa);
      color: white;
      border: none;
      border-radius: 32px;
      cursor: pointer;
      box-shadow: 0 8px 20px rgba(233, 30, 99, 0.4);
      transition: all 0.3s ease;
      animation: float 3s ease-in-out infinite;
    }

    @keyframes float {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-6px); }
    }

    /* Contenedor principal - Carta */
    .main-container {
      display: none;
      text-align: center;
      max-width: 95%;
      padding: 1.8rem 1.4rem;
    }

    .letter-frame {
      background: rgba(255, 255, 255, 0.95);
      border-radius: 30px;
      padding: 1.8rem 1.6rem;
      box-shadow: 0 15px 40px rgba(255, 105, 180, 0.25);
      border: 4px solid transparent;
      background-clip: padding-box;
      position: relative;
      margin-bottom: 1.6rem;
    }

    .letter-frame::before {
      content: '';
      position: absolute;
      inset: 0;
      border-radius: 30px;
      padding: 4px;
      background: linear-gradient(45deg, #ff80ab, #ba68c8);
      -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
      -webkit-mask-composite: destination-out;
      mask-composite: subtract;
      pointer-events: none;
    }

    h1 {
      font-family: 'Playfair Display', serif;
      font-size: 2.3rem;
      background: linear-gradient(45deg, #e91e63, #ba68c8);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      margin-bottom: 1.4rem;
    }

    .letter {
      font-family: 'Dancing Script', cursive;
      font-size: 1.55rem;
      line-height: 1.65;
      color: #d81b60;
      text-align: left;
      white-space: pre-line;
      letter-spacing: 0.8px;
      margin: 0;
      opacity: 1;
      font-weight: 500;
    }

    .btn-gallery {
      display: inline-block;
      margin: 1.4rem auto 1rem;
      padding: 0.9rem 2rem;
      font-family: 'Poppins', sans-serif;
      font-size: 1.15rem;
      font-weight: 600;
      color: white;
      background: linear-gradient(45deg, #e91e63, #ba68c8);
      border: none;
      border-radius: 30px;
      cursor: pointer;
      box-shadow: 0 8px 20px rgba(233, 30, 99, 0.4);
      transition: all 0.3s ease;
      animation: pulse 2s infinite, rainbowGlow 3s ease-in-out infinite alternate;
    }

    .btn-gallery:hover {
      transform: scale(1.12);
      box-shadow: 0 10px 25px rgba(233, 30, 99, 0.6);
    }

    footer {
      margin-top: 1.4rem;
      font-style: italic;
      color: #ba68c8;
      font-size: 1.1rem;
    }

    /* Galería */
    .gallery-screen {
      display: none;
      flex-direction: column;
      align-items: center;
      width: 100%;
      max-width: 900px;
      padding: 2rem 1.4rem;
      text-align: center;
    }

    .gallery-title {
      font-family: 'Playfair Display', serif;
      font-size: 2.5rem;
      background: linear-gradient(45deg, #e91e63, #ba68c8, #ff8f00);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      margin-bottom: 1.6rem;
      animation: rainbowGlow 3s ease-in-out infinite alternate;
    }

    .gallery-main-img {
      width: 100%;
      max-width: 480px;
      margin-bottom: 1.8rem;
    }

    .gallery-thumbnails {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(110px, 1fr));
      gap: 10px;
      width: 100%;
      max-width: 580px;
    }

    /* Modal de zoom */
    .modal-zoom {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.9);
      z-index: 2000;
      justify-content: center;
      align-items: center;
      cursor: zoom-out;
    }

    .modal-zoom img {
      max-width: 90%;
      max-height: 90%;
      border-radius: 15px;
      border: 5px solid #e91e63;
      box-shadow: 0 0 30px rgba(255, 105, 180, 0.8);
      animation: fadeIn 0.3s;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: scale(0.9); }
      to { opacity: 1; transform: scale(1); }
    }

    /* Cuadro de error */
    .error-modal {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.5);
      display: flex;
      justify-content: center;
      align-items: center;
      z-index: 200;
      opacity: 0;
      pointer-events: none;
      transition: opacity 0.3s;
    }

    .error-modal.active {
      opacity: 1;
      pointer-events: all;
    }

    .error-content {
      background: white;
      border-radius: 20px;
      width: 90%;
      max-width: 360px;
      padding: 1.6rem;
      position: relative;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
      border: 3px solid #ffb6c1;
      animation: popIn 0.3s;
      font-family: 'Poppins', sans-serif;
    }

    @keyframes popIn {
      from { transform: scale(0.8); opacity: 0; }
      to { transform: scale(1); opacity: 1; }
    }

    .close-error {
      position: absolute;
      top: 10px;
      right: 10px;
      font-size: 1.4rem;
      color: #e91e63;
      cursor: pointer;
      width: 26px;
      height: 26px;
      display: flex;
      justify-content: center;
      align-items: center;
      border-radius: 50%;
      background: #fff0f5;
      transition: all 0.2s;
    }

    .close-error:hover {
      background: #ffe6f0;
      transform: rotate(90deg);
    }

    .error-content h3 {
      color: #e91e63;
      margin-bottom: 0.9rem;
      font-size: 1.25rem;
      text-align: center;
    }

    .error-content p {
      color: #555;
      line-height: 1.55;
      margin-bottom: 1.3rem;
      font-size: 1.02rem;
    }

    /* Corazones flotantes */
    .floating-heart {
      position: fixed;
      font-size: 18px;
      pointer-events: none;
      opacity: 0;
      z-index: 1000;
      user-select: none;
      animation: floatUp 18s ease-out forwards, fadeHeart 4s ease-in-out infinite;
    }

    @keyframes floatUp {
      0% {
        transform: translateY(100vh) rotate(0deg);
        opacity: 0;
      }
      10% { opacity: 0.8; }
      90% { opacity: 0.8; }
      100% {
        transform: translateY(-20vh) rotate(360deg);
        opacity: 0;
      }
    }

    @keyframes fadeHeart {
      0%, 100% { opacity: 0.6; }
      50% { opacity: 1; }
    }

    .credit {
      margin-top: 1.3rem;
      font-size: 0.7rem;
      color: #ccc;
      font-style: italic;
      text-align: center;
    }

    /* Responsive */
    @media (max-width: 480px) {
      .create-screen, .lock-screen, .main-container, .gallery-screen {
        padding: 1.4rem;
        max-width: 98%;
      }

      h1 {
        font-size: 2rem;
      }

      .letter {
        font-size: 1.4rem;
        line-height: 1.6;
      }

      .btn-iniciar {
        font-size: 1.15rem;
        padding: 0.8rem 1.8rem;
      }
    }
  </style>
</head>
<body>

  <!-- Corazones flotantes -->
  <script>
    function createHearts() {
      const hearts = ['❤️', '💖', '💕', '💓', '💗', '💞', '💘', '💝', '💟'];
      setInterval(() => {
        const heart = document.createElement('div');
        heart.className = 'floating-heart';
        heart.textContent = hearts[Math.floor(Math.random() * hearts.length)];
        heart.style.left = Math.random() * 90 + 5 + 'vw';
        heart.style.bottom = '0';
        document.body.appendChild(heart);
        setTimeout(() => heart.remove(), 18000);
      }, 2500);
    }
    createHearts();
  </script>

  <!-- Pantalla de creación -->
  <div id="createScreen" class="create-screen">
    <h2>✨ Crea tu Detalle Virtual</h2>
    <p>Rellena todo y genera tu link personalizado</p>

    <div class="form-group">
      <label>💌 Para: Nombre de tu amor</label>
      <input type="text" id="nombreElla" placeholder="Ej: María" />
    </div>

    <div class="form-group">
      <label>👨‍❤️‍💋‍👨 De: Tu nombre</label>
      <input type="text" id="nombreYo" placeholder="Ej: Juan" />
    </div>

    <div class="form-group">
      <label>✍️ Tu mensaje (puedes usar saltos de línea)</label>
      <textarea id="mensaje" placeholder="Mi amor, desde que te conocí..."></textarea>
    </div>

    <div class="form-group">
      <label>🔐 Código de acceso (ej: 12/25)</label>
      <input type="text" id="codigoAcceso" placeholder="Ej: 14/02" value="14/02" />
    </div>

    <div class="form-group">
      <label>🖼️ URL de foto principal</label>
      <input type="url" id="fotoPrincipal" placeholder="https://ejemplo.com/foto.jpg" />
    </div>

    <div class="form-group">
      <label>🖼️ URLs de fotos para galería (una por línea)</label>
      <textarea id="fotosGaleria" placeholder="https://ejemplo.com/foto1.jpg
https://ejemplo.com/foto2.jpg"></textarea>
    </div>

    <button onclick="generarLink()">Generar Link 🌟</button>
  </div>

  <!-- Pantalla de bloqueo (se mostrará después) -->
  <div id="lockScreen" class="lock-screen" style="display:none;">
    <h2>🔐 Tu Carta Mi Amor</h2>
    <p>👇 INGRESA EL CÓDIGO DE ACCESO 👇</p>

    <div class="glow-frame">
      <img src="https://media2.giphy.com/media/v1.Y2lkPTZjMDliOTUyZTAxbHV0Mm1rYmI2emc3ZmdvcGdka2szMGMzMHl4ZXlhcmEzN3A4cCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/Y62ofc4S1Vst2/giphy.gif" alt="Corazones flotando" />
    </div>

    <div id="display" class="key-display"></div>

    <div class="keypad">
      <div class="key" onclick="addDigit('1')">1</div>
      <div class="key" onclick="addDigit('2')">2</div>
      <div class="key" onclick="addDigit('3')">3</div>
      <div class="key" onclick="addDigit('4')">4</div>
      <div class="key" onclick="addDigit('5')">5</div>
      <div class="key" onclick="addDigit('6')">6</div>
      <div class="key" onclick="addDigit('7')">7</div>
      <div class="key" onclick="addDigit('8')">8</div>
      <div class="key" onclick="addDigit('9')">9</div>
      <div class="key" onclick="addDigit('0')">0</div>
      <div class="key" onclick="addDigit('/')">/</div>
      <div class="key" onclick="clearInput()">⌫</div>
    </div>

    <button class="btn-iniciar" onclick="submitKey()">Iniciar</button>

    <div class="glow-frame">
      <img src="https://media0.giphy.com/media/v1.Y2lkPTZjMDliOTUyMzl0NTh2ZHhmOHF1Nm45NHNqcmN1bTVrdHNtbDgwbjZpZTFqMno3diZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/11TyfGbDbBv4be/giphy.gif" alt="Bailarina de amor" />
    </div>
  </div>

  <!-- Carta principal -->
  <div id="mainContainer" class="main-container">
    <div class="letter-frame">
      <h1 id="tituloCarta"></h1>
      <div id="letter" class="letter"></div>

      <div class="glow-frame" style="margin: 1.4rem auto; max-width: 400px; display: flex; justify-content: center;">
        <img id="fotoPrincipalMostrada" src="" alt="Foto principal" />
      </div>

      <button class="btn-gallery" onclick="openGallery()">Ver nuestras fotos 📸</button>
      <footer id="firmaCarta"></footer>
    </div>
    <p class="credit">By AnthZz Berrocal BerMatMods</p>
  </div>

  <!-- Galería -->
  <div id="galleryScreen" class="gallery-screen">
    <h2 class="gallery-title">✨ Nuestra Galería</h2>

    <div class="glow-frame gallery-main-img">
      <img id="mainGalleryImg" src="" style="width: 100%; border-radius: 18px;" onclick="zoomImage(this)" />
    </div>

    <div class="gallery-thumbnails" id="thumbnailsContainer"></div>

    <button class="btn-iniciar" style="margin-top: 1.8rem;" onclick="closeGallery()">Volver a la carta</button>
    <p class="credit">By AnthZz Berrocal BerMatMods</p>
  </div>

  <!-- Modal de zoom -->
  <div id="zoomModal" class="modal-zoom" onclick="closeZoom()">
    <img id="zoomedImage" src="" />
  </div>

  <!-- Error -->
  <div id="errorModal" class="error-modal">
    <div class="error-content">
      <div class="close-error" onclick="cerrarError()">×</div>
      <h3>⚠️ Código Incorrecto</h3>
      <p>El código que ingresaste es incorrecto. Por favor, inténtalo de nuevo.</p>
    </div>
  </div>

  <script>
    let input = '';
    let data = {};

    function addDigit(digit) {
      if (input.length < 10) {
        input += digit;
        document.getElementById('display').textContent = input;
      }
    }

    function clearInput() {
      input = '';
      document.getElementById('display').textContent = '';
    }

    function cerrarError() {
      document.getElementById('errorModal').classList.remove('active');
    }

    function submitKey() {
      if (input === data.codigoAcceso) {
        document.getElementById('lockScreen').style.display = 'none';
        document.getElementById('mainContainer').style.display = 'block';
        mostrarCarta();
      } else {
        document.getElementById('errorModal').classList.add('active');
        clearInput();
      }
    }

    function mostrarCarta() {
      document.getElementById('tituloCarta').textContent = `Para Ti ${data.nombreElla} 💖`;
      document.getElementById('firmaCarta').textContent = `Con todo mi corazón, ${data.nombreYo}`;
      document.getElementById('fotoPrincipalMostrada').src = data.fotoPrincipal;

      const letter = document.getElementById('letter');
      letter.textContent = '';
      let i = 0;
      const speed = 35;
      function type() {
        if (i < data.mensaje.length) {
          letter.textContent += data.mensaje.charAt(i);
          i++;
          setTimeout(type, speed);
        }
      }
      setTimeout(type, 300);
    }

    function openGallery() {
      const fotos = data.fotosGaleria.split('\n').filter(f => f.trim() !== '');
      if (fotos.length > 0) {
        document.getElementById('mainGalleryImg').src = fotos[0];
        const thumbs = document.getElementById('thumbnailsContainer');
        thumbs.innerHTML = '';
        fotos.forEach(foto => {
          const div = document.createElement('div');
          div.className = 'glow-frame';
          const img = document.createElement('img');
          img.src = foto;
          img.className = 'gallery-img';
          img.onclick = () => document.getElementById('mainGalleryImg').src = foto;
          div.appendChild(img);
          thumbs.appendChild(div);
        });
      }
      document.getElementById('mainContainer').style.display = 'none';
      document.getElementById('galleryScreen').style.display = 'flex';
    }

    function closeGallery() {
      document.getElementById('galleryScreen').style.display = 'none';
      document.getElementById('mainContainer').style.display = 'block';
    }

    function zoomImage(img) {
      document.getElementById('zoomedImage').src = img.src;
      document.getElementById('zoomModal').style.display = 'flex';
    }

    function closeZoom() {
      document.getElementById('zoomModal').style.display = 'none';
    }

    // Generar link
    function generarLink() {
      const nombreElla = document.getElementById('nombreElla').value.trim();
      const nombreYo = document.getElementById('nombreYo').value.trim();
      const mensaje = document.getElementById('mensaje').value.trim();
      const codigoAcceso = document.getElementById('codigoAcceso').value.trim();
      const fotoPrincipal = document.getElementById('fotoPrincipal').value.trim() || 'https://via.placeholder.com/400x300?text=Foto+Principal';
      const fotosGaleria = document.getElementById('fotosGaleria').value.trim() || '';

      if (!nombreElla || !nombreYo || !mensaje || !codigoAcceso) {
        alert('Completa todos los campos');
        return;
      }

      data = { nombreElla, nombreYo, mensaje, codigoAcceso, fotoPrincipal, fotosGaleria };
      const id = Math.random().toString(36).substr(2, 6);
      localStorage.setItem('detalle_' + id, JSON.stringify(data));

      const link = `${window.location.href.split('#')[0]}#${id}`;
      alert(`✅ Link generado:\n\n${link}\n\nPuedes copiarlo y enviarlo por WhatsApp.`);
      prompt('Link para compartir:', link);
    }

    // Cargar detalle si hay hash
    window.addEventListener('load', () => {
      const hash = window.location.hash.slice(1);
      if (hash) {
        const saved = localStorage.getItem('detalle_' + hash);
        if (saved) {
          data = JSON.parse(saved);
          document.getElementById('createScreen').style.display = 'none';
          document.getElementById('lockScreen').style.display = 'block';
          document.getElementById('display').textContent = '';
        } else {
          alert('❌ Detalle no encontrado. Puede que haya sido eliminado.');
        }
      }
    });
  </script>
</body>
</html>
