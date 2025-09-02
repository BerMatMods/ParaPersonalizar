
<html lang="es" id="htmlLang">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no" />
  <title>Detalles Virtuales - Tu Carta de Amor</title>

  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Playfair+Display:wght@700&family=Poppins:wght@400;500&family=Quicksand:wght@500&display=swap" rel="stylesheet">

  <style>
    :root {
      --primary: #9c27b0;
      --secondary: #e91e63;
      --light: #f8f0f7;
      --dark: #333;
      --text-light: #fff;
      --bg-gradient: linear-gradient(135deg, #f8f0f7, #eadcf4, #f3e1f8);
      --card-bg: rgba(255, 255, 255, 0.94);
      --border-glow: 0 0 20px rgba(156, 39, 176, 0.6);
      --border: 3px solid var(--primary);
    }

    .dark-mode {
      --primary: #ba68c8;
      --secondary: #ec407a;
      --light: #2e1a3a;
      --dark: #e0e0e0;
      --text-light: #fff;
      --bg-gradient: linear-gradient(135deg, #2e1a3a, #3a214a, #4a2d5a);
      --card-bg: rgba(40, 25, 45, 0.88);
      --border-glow: 0 0 20px rgba(236, 64, 122, 0.7);
      --border: 3px solid var(--primary);
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      transition: background 0.4s, color 0.4s, box-shadow 0.3s;
    }

    body {
      font-family: 'Poppins', sans-serif;
      background: var(--bg-gradient);
      color: var(--dark);
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
      0% { box-shadow: 0 0 15px rgba(156, 39, 176, 0.7); }
      25% { box-shadow: 0 0 15px rgba(233, 30, 99, 0.7); }
      50% { box-shadow: 0 0 15px rgba(0, 200, 255, 0.7); }
      75% { box-shadow: 0 0 15px rgba(255, 190, 100, 0.7); }
      100% { box-shadow: 0 0 15px rgba(156, 39, 176, 0.7); }
    }

    .glow-frame {
      position: relative;
      display: inline-block;
      border-radius: 20px;
      margin: 1rem 0;
      animation: rainbowGlow 3s ease-in-out infinite alternate;
      background: linear-gradient(45deg, #9c27b0, #ba68c8, #ec407a, #ff80ab);
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

    /* Menú de tres rayas */
    .menu-btn {
      position: fixed;
      top: 20px;
      left: 20px;
      cursor: pointer;
      z-index: 100;
      width: 40px;
      height: 40px;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      background: var(--card-bg);
      padding: 8px;
      border-radius: 12px;
      box-shadow: var(--border-glow);
    }

    .menu-btn span {
      display: block;
      width: 100%;
      height: 4px;
      background: var(--primary);
      border-radius: 2px;
      transition: 0.3s;
    }

    .menu {
      position: fixed;
      top: 0;
      left: -320px;
      width: 300px;
      height: 100vh;
      background: var(--card-bg);
      border-right: var(--border);
      box-shadow: var(--border-glow);
      transition: left 0.4s ease;
      z-index: 1000;
      padding: 20px;
      overflow-y: auto;
    }

    .menu.active {
      left: 0;
    }

    .close-btn {
      position: absolute;
      top: 20px;
      right: 20px;
      font-size: 1.8em;
      color: var(--primary);
      cursor: pointer;
      background: none;
      border: none;
    }

    /* Perfil en menú */
    .menu-profile {
      text-align: center;
      padding: 20px 0;
      margin-bottom: 20px;
      border-bottom: 2px solid var(--primary);
    }

    .menu-profile img {
      width: 80px;
      height: 80px;
      border-radius: 50%;
      border: 3px solid var(--primary);
      object-fit: cover;
      margin-bottom: 10px;
      box-shadow: 0 0 15px rgba(156, 39, 176, 0.4);
    }

    .menu-profile h3 {
      color: var(--primary);
      font-family: 'Playfair Display', serif;
      margin: 10px 0;
      font-size: 1.3em;
    }

    .menu-profile p {
      color: var(--dark);
      font-size: 0.9em;
    }

    .menu-title {
      text-align: center;
      color: var(--primary);
      font-family: 'Playfair Display', serif;
      margin-bottom: 20px;
      font-size: 1.5em;
    }

    .menu-grid {
      display: grid;
      grid-template-columns: 1fr;
      gap: 12px;
    }

    .menu-item {
      background: var(--card-bg);
      border: 2px solid var(--primary);
      border-radius: 16px;
      padding: 14px;
      text-align: center;
      color: var(--primary);
      font-weight: 600;
      cursor: pointer;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
      animation: rainbowGlow 3s ease-in-out infinite alternate;
    }

    /* Modal: Requisito de TikTok */
    .modal-tiktok {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.6);
      z-index: 1000;
      justify-content: center;
      align-items: center;
      animation: fadeIn 0.4s;
    }

    .modal-tiktok-content {
      background: var(--card-bg);
      border-radius: 20px;
      padding: 25px;
      max-width: 400px;
      width: 90%;
      text-align: center;
      box-shadow: 0 10px 40px rgba(0,0,0,0.2);
      border: var(--border);
      position: relative;
      animation: popIn 0.4s;
    }

    .modal-tiktok-close {
      position: absolute;
      top: 15px;
      right: 15px;
      font-size: 1.4em;
      color: var(--primary);
      cursor: pointer;
      background: #fff;
      width: 30px;
      height: 30px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .modal-tiktok-title {
      color: var(--primary);
      font-family: 'Playfair Display', serif;
      margin-bottom: 15px;
      font-size: 1.5em;
    }

    .btn-tiktok {
      margin: 15px auto;
      padding: 12px 20px;
      background: #000000;
      color: white;
      border: none;
      border-radius: 12px;
      cursor: pointer;
      font-size: 1.1em;
      font-weight: 600;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
      width: 80%;
      max-width: 300px;
    }

    .btn-tiktok::before {
      content: "🎵";
    }

    /* Modal: Error si no sigue */
    .modal-error {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.6);
      z-index: 1000;
      justify-content: center;
      align-items: center;
    }

    .modal-error-content {
      background: var(--card-bg);
      border-radius: 20px;
      padding: 25px;
      max-width: 400px;
      width: 90%;
      text-align: center;
      box-shadow: 0 10px 40px rgba(0,0,0,0.2);
      border: 3px solid #e91e63;
      position: relative;
      animation: popIn 0.4s;
    }

    .modal-error-close {
      position: absolute;
      top: 15px;
      right: 15px;
      font-size: 1.4em;
      color: #e91e63;
      cursor: pointer;
      background: #fff0f5;
      width: 30px;
      height: 30px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .modal-error h3 {
      color: #e91e63;
      margin-bottom: 12px;
      font-size: 1.3em;
    }

    .modal-error p {
      color: var(--dark);
      line-height: 1.6;
      font-size: 0.95em;
    }

    /* Animaciones */
    @keyframes fadeIn {
      from { opacity: 0; }
      to { opacity: 1; }
    }

    @keyframes popIn {
      from { transform: scale(0.8); opacity: 0; }
      to { transform: scale(1); opacity: 1; }
    }

    /* Pantalla de creación */
    .create-screen {
      text-align: center;
      padding: 1.8rem 2rem;
      max-width: 480px;
      background: var(--card-bg);
      border-radius: 32px;
      box-shadow: 0 16px 45px rgba(0,0,0,0.15);
      border: var(--border);
      position: relative;
      z-index: 1;
      margin-bottom: 25px;
    }

    .create-screen h2 {
      font-family: 'Playfair Display', serif;
      font-size: 2.1rem;
      color: var(--primary);
      margin: 1rem 0;
    }

    .form-group {
      margin: 1.2rem 0;
    }

    label {
      display: block;
      text-align: left;
      margin-bottom: 8px;
      color: var(--primary);
      font-weight: 600;
      font-size: 0.95em;
    }

    input, textarea, select {
      width: 100%;
      padding: 10px 12px;
      border: 2px solid var(--primary);
      border-radius: 14px;
      font-size: 1em;
      background: rgba(255,255,255,0.7);
      color: var(--dark);
      font-family: inherit;
    }

    button {
      margin: 1.3rem auto;
      padding: 0.9rem 2rem;
      font-size: 1.25rem;
      font-weight: 600;
      background: linear-gradient(45deg, var(--primary), var(--secondary));
      color: white;
      border: none;
      border-radius: 32px;
      cursor: pointer;
      box-shadow: 0 8px 20px rgba(156, 39, 176, 0.4);
      transition: all 0.3s ease;
      display: block;
    }

    /* Cuadro de link generado */
    .link-box {
      display: none;
      margin: 20px auto;
      padding: 20px;
      background: var(--card-bg);
      border-radius: 20px;
      box-shadow: var(--border-glow);
      max-width: 460px;
      text-align: center;
      border: var(--border);
      animation: fadeIn 0.5s;
    }

    .link-box h3 {
      color: var(--primary);
      font-family: 'Playfair Display', serif;
      margin-bottom: 12px;
    }

    .link-box input {
      width: 100%;
      margin: 12px 0;
      padding: 14px;
      border: 2px solid var(--primary);
      border-radius: 14px;
      font-size: 1em;
      text-align: center;
      background: rgba(255,255,255,0.8);
      color: var(--primary);
      font-family: monospace;
      letter-spacing: 1px;
    }

    .link-actions {
      display: flex;
      justify-content: center;
      gap: 12px;
      flex-wrap: wrap;
    }

    .link-actions button {
      margin: 0;
      padding: 10px 18px;
      font-size: 1em;
      background: var(--secondary);
      width: auto;
    }

    /* Pantalla de bloqueo */
    .lock-screen {
      display: none;
      text-align: center;
      padding: 1.8rem 2rem;
      max-width: 440px;
      background: var(--card-bg);
      border-radius: 32px;
      box-shadow: 0 16px 45px rgba(0,0,0,0.15);
      border: var(--border);
      position: relative;
      z-index: 1;
    }

    .lock-screen h2 {
      font-family: 'Playfair Display', serif;
      font-size: 2.1rem;
      color: var(--primary);
      margin: 1rem 0;
      animation: rainbowGlow 3s ease-in-out infinite alternate;
    }

    .lock-screen p {
      color: var(--primary);
      font-size: 1.15rem;
      margin-bottom: 1.3rem;
      font-weight: 500;
    }

    .key-display {
      font-family: 'Poppins', monospace;
      font-size: 1.8rem;
      color: var(--primary);
      background: rgba(255,255,255,0.7);
      padding: 0.9rem 1.3rem;
      border-radius: 16px;
      margin: 1.1rem auto;
      width: 90%;
      border: 2px solid var(--primary);
      letter-spacing: 4px;
      box-shadow: 0 6px 15px rgba(156, 39, 176, 0.2);
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
      background: rgba(255,255,255,0.7);
      color: var(--primary);
      border: 2px solid var(--primary);
      border-radius: 14px;
      cursor: pointer;
      transition: all 0.25s;
      box-shadow: 0 4px 10px rgba(156, 39, 176, 0.1);
    }

    .key:hover {
      transform: translateY(-3px);
      box-shadow: 0 6px 15px rgba(156, 39, 176, 0.2);
    }

    /* Contenedor principal - Carta */
    .main-container {
      display: none;
      text-align: center;
      max-width: 95%;
      padding: 1.8rem 1.4rem;
    }

    .letter-frame {
      background: var(--card-bg);
      border-radius: 30px;
      padding: 1.8rem 1.6rem;
      box-shadow: 0 15px 40px rgba(0,0,0,0.15);
      border: var(--border);
      position: relative;
      margin-bottom: 1.6rem;
    }

    h1 {
      font-family: 'Playfair Display', serif;
      font-size: 2.3rem;
      color: var(--primary);
      margin-bottom: 1.4rem;
    }

    .letter {
      font-family: 'Dancing Script', cursive;
      font-size: 1.55rem;
      line-height: 1.65;
      color: var(--primary);
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
      background: linear-gradient(45deg, var(--primary), var(--secondary));
      border: none;
      border-radius: 30px;
      cursor: pointer;
      box-shadow: 0 8px 20px rgba(156, 39, 176, 0.4);
      transition: all 0.3s ease;
      animation: rainbowGlow 3s ease-in-out infinite alternate;
    }

    footer {
      margin-top: 1.4rem;
      font-style: italic;
      color: var(--primary);
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
      color: var(--primary);
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
      border: 5px solid var(--primary);
      box-shadow: 0 0 30px rgba(156, 39, 176, 0.8);
      animation: fadeIn 0.3s;
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
      box-shadow: 0 10px 30px rgba(0,0,0,0.15);
      border: 3px solid #ffb6c1;
      font-family: 'Poppins', sans-serif;
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

    /* Créditos */
    .credit {
      margin-top: 25px;
      padding: 15px;
      font-size: 0.9em;
      color: var(--primary);
      font-weight: 600;
      text-align: center;
      font-style: italic;
      background: var(--card-bg);
      border-radius: 18px;
      border: 2px solid var(--primary);
      box-shadow: var(--border-glow);
      max-width: 400px;
      width: 90%;
    }

    /* Botón para volver a personalizar */
    .btn-recreate {
      margin-top: 1.4rem;
      padding: 0.9rem 2rem;
      font-size: 1.15rem;
      font-weight: 600;
      color: white;
      background: linear-gradient(45deg, #4a148c, #7b1fa2);
      border: none;
      border-radius: 30px;
      cursor: pointer;
      box-shadow: 0 8px 20px rgba(74, 20, 140, 0.4);
      transition: all 0.3s ease;
    }

    .btn-recreate:hover {
      transform: scale(1.05);
    }

    /* Responsive */
    @media (max-width: 480px) {
      .create-screen, .lock-screen, .main-container, .gallery-screen, .credit {
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

      .btn-gallery, .btn-recreate, .btn-tiktok {
        font-size: 1.1rem;
      }
    }
  </style>
</head>
<body>

  <!-- Menú de tres rayas -->
  <div class="menu-btn" id="menuBtn">
    <span></span>
    <span></span>
    <span></span>
  </div>

  <div class="menu" id="menu">
    <div class="close-btn" id="closeMenu">&times;</div>

    <!-- Perfil en menú -->
    <div class="menu-profile">
      <img src="https://i.postimg.cc/CKMXCWTj/Screenshot-20250826-182522.jpg" alt="AnthZz Berrocal">
      <h3>AnthZz Berrocal</h3>
      <p>BerMatMods • Desarrollador</p>
    </div>

    <h3 class="menu-title">🔧 Ajustes</h3>
    <div class="menu-grid">
      <div class="menu-item" onclick="openModal('langModal')">🌐 Idioma</div>
      <div class="menu-item" onclick="openModal('themeModal')">🌙 Tema</div>
      <div class="menu-item" onclick="openModal('infoModal')">ℹ️ Información</div>
      <div class="menu-item" onclick="openModal('contactModal')">📞 Contacto</div>
      <div class="menu-item" onclick="toggleMusic()">🎵 Música</div>
      <div class="menu-item" onclick="toggleNotifications()">🔔 Notificaciones</div>
      <div class="menu-item" onclick="optimizeMobile()">📱 Modo Móvil</div>
    </div>
  </div>

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

  <!-- Modal: Requisito TikTok -->
  <div id="modalTiktok" class="modal-tiktok">
    <div class="modal-tiktok-content">
      <div class="modal-tiktok-close" onclick="closeModalTiktok()">×</div>
      <h3 class="modal-tiktok-title">🔔 ¡Importante!</h3>
      <p style="color:var(--dark); margin:10px 0;">
        Para crear tu detalle personalizado, primero debes seguir a mi cuenta de TikTok.
      </p>
      <a href="https://www.tiktok.com/@bermat_mods?_t=ZS-8zNqlsUAY7t&_r=1" target="_blank" class="btn-tiktok" onclick="seguirTikTok()">
        Seguir en TikTok
      </a>
      <p style="font-size:0.9em; color:var(--primary); margin-top:10px;">@bermat_mods</p>
    </div>
  </div>

  <!-- Modal: Error si no sigue -->
  <div id="modalError" class="modal-error">
    <div class="modal-error-content">
      <div class="modal-error-close" onclick="closeModalError()">×</div>
      <h3>⚠️ Acceso Denegado</h3>
      <p>
        El sistema de <strong>BerMatMods</strong> ha detectado que no has seguido la cuenta de TikTok.
        <br><br>
        Por lo tanto, no se podrá generar tu enlace de detalle personalizado.
        <br><br>
        Inténtalo más tarde.
      </p>
    </div>
  </div>

  <!-- Pantalla de creación -->
  <div id="createScreen" class="create-screen">
    <h2 id="createTitle">✨ Crea tu Detalle Virtual</h2>
    <p id="createSubtitle">Llena todo y genera tu link personalizado ❤️</p>

    <div class="form-group">
      <label id="labelPara">💌 Para: Nombre de tu amor</label>
      <input type="text" id="nombreElla" placeholder="Ej: Jhorgina Briyidth" required />
    </div>

    <div class="form-group">
      <label id="labelDe">👨‍❤️‍💋‍👨 De: Tu nombre</label>
      <input type="text" id="nombreYo" placeholder="Ej: AnthZz Berrocal" required />
    </div>

    <div class="form-group">
      <label id="labelMensaje">✍️ Tu mensaje (usa saltos de línea)</label>
      <textarea id="mensaje" placeholder="Mi amor, desde que te conocí..." required></textarea>
    </div>

    <div class="form-group">
      <label id="labelFuente">🎨 Tipo de letra</label>
      <select id="fuenteTexto">
        <option value="'Dancing Script', cursive">Elegante (Script)</option>
        <option value="'Quicksand', sans-serif">Moderna (Quicksand)</option>
        <option value="'Poppins', sans-serif">Clara (Poppins)</option>
        <option value="Arial, sans-serif">Simple (Arial)</option>
      </select>
    </div>

    <div class="form-group">
      <label id="labelColor">🌈 Color del texto</label>
      <select id="colorTexto">
        <option value="#9c27b0">Morado</option>
        <option value="#e91e63">Rosa</option>
        <option value="#8B0000">Rojo</option>
        <option value="#4B0082">Índigo</option>
        <option value="#2F4F4F">Verde</option>
      </select>
    </div>

    <div class="form-group">
      <label id="labelCodigo">🔐 Código de acceso (ej: 10/11/23)</label>
      <input type="text" id="codigoAcceso" placeholder="Ej: 10/11/23" value="10/11/23" required />
    </div>

    <div class="form-group">
      <label id="labelFoto">🖼️ URL de foto principal</label>
      <input type="url" id="fotoPrincipal" placeholder="https://ejemplo.com/foto.jpg" />
    </div>

    <div class="form-group">
      <label id="labelGaleria">🖼️ URLs de fotos para galería (una por línea)</label>
      <textarea id="fotosGaleria" placeholder="https://ejemplo.com/foto1.jpg
https://ejemplo.com/foto2.jpg"></textarea>
    </div>

    <button onclick="checkTikTokFollow()">Generar Link 🌟</button>

    <!-- Cuadro de link generado -->
    <div class="link-box" id="linkBox">
      <h3 id="linkTitle">🔗 Tu link está listo</h3>
      <input type="text" id="linkInput" readonly />
      <div class="link-actions">
        <button onclick="copyLink()"><span id="btnCopiar">📋 Copiar Link</span></button>
        <button onclick="shareOnWhatsApp()"><span id="btnWhatsApp">💬 Enviar por WhatsApp</span></button>
      </div>
    </div>
  </div>

  <!-- Pantalla de bloqueo -->
  <div id="lockScreen" class="lock-screen">
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

      <button class="btn-recreate" onclick="volverACrear()">🔄 Volver a personalizar</button>
    </div>
    <p class="credit">Desarrollado por AnthZz Berrocal | BerMatMods</p>
  </div>

  <!-- Galería -->
  <div id="galleryScreen" class="gallery-screen">
    <h2 class="gallery-title">✨ Nuestra Galería</h2>

    <div class="glow-frame gallery-main-img">
      <img id="mainGalleryImg" src="" style="width: 100%; border-radius: 18px;" onclick="zoomImage(this)" />
    </div>

    <div class="gallery-thumbnails" id="thumbnailsContainer"></div>

    <button class="btn-iniciar" style="margin-top: 1.8rem;" onclick="closeGallery()">Volver a la carta</button>
    <p class="credit">Desarrollado por AnthZz Berrocal | BerMatMods</p>
  </div>

  <!-- Modal de zoom -->
  <div id="zoomModal" class="modal-zoom" onclick="closeZoom()">
    <img id="zoomedImage" src="" />
  </div>

  <!-- Cuadro de error -->
  <div id="errorModal" class="error-modal">
    <div class="error-content">
      <div class="close-error" onclick="cerrarError()">×</div>
      <h3>⚠️ Código Incorrecto</h3>
      <p>El código que ingresaste es incorrecto. Por favor, inténtalo de nuevo.</p>
    </div>
  </div>

  <!-- Modales -->
  <div id="langModal" class="modal">
    <div class="modal-content">
      <div class="modal-close" onclick="closeModal('langModal')">×</div>
      <h3 class="modal-title">🌐 Idioma</h3>
      <p>Selecciona tu idioma:</p>
      <button class="modal-btn" onclick="setLang('es'); closeModal('langModal')">Español</button>
      <button class="modal-btn" onclick="setLang('en'); closeModal('langModal')">English</button>
      <button class="modal-btn" onclick="setLang('pt'); closeModal('langModal')">Português</button>
    </div>
  </div>

  <div id="themeModal" class="modal">
    <div class="modal-content">
      <div class="modal-close" onclick="closeModal('themeModal')">×</div>
      <h3 class="modal-title">🎨 Tema</h3>
      <p>Elige tu modo:</p>
      <button class="modal-btn" onclick="setTheme('light'); closeModal('themeModal')">Claro</button>
      <button class="modal-btn" onclick="setTheme('dark'); closeModal('themeModal')">Oscuro</button>
    </div>
  </div>

  <div id="infoModal" class="modal">
    <div class="modal-content">
      <div class="modal-close" onclick="closeModal('infoModal')">×</div>
      <h3 class="modal-title">ℹ️ Información</h3>
      <div style="text-align: center; margin: 15px 0;">
        <img src="https://i.postimg.cc/CKMXCWTj/Screenshot-20250826-182522.jpg" alt="AnthZz Berrocal" style="width: 80px; height: 80px; border-radius: 50%; border: 3px solid #9c27b0; object-fit: cover;">
        <p style="color:var(--dark); text-align:left; margin:10px 0; font-size:0.95em;">
          <strong>Nombre:</strong> AnthZz Berrocal<br>
          <strong>Alias:</strong> BerMatMods<br>
          <strong>Desarrollador Web</strong><br>
          <strong>País:</strong> Perú
        </p>
      </div>
      <button class="modal-btn" onclick="closeModal('infoModal')">Cerrar</button>
    </div>
  </div>

  <div id="contactModal" class="modal">
    <div class="modal-content">
      <div class="modal-close" onclick="closeModal('contactModal')">×</div>
      <h3 class="modal-title">📞 Contacto Directo</h3>
      <p style="color:var(--dark);">¿Quieres un detalle más personalizado?</p>
      <a href="https://wa.me/51937556459?text=Hola%20AnthZz,%20quiero%20un%20detalle%20personalizado" target="_blank" style="margin:15px auto; padding:12px 20px; background:var(--secondary); color:white; text-decoration:none; border-radius:12px; display:inline-block;">
        💬 Chatear por WhatsApp
      </a>
      <p style="font-size:0.9em; color:var(--primary); margin-top:10px;">+51 937 556 459</p>
    </div>
  </div>

  <script>
    let input = '';
    let data = {};
    let currentLang = 'es';
    let currentTheme = 'light';
    let tikTokFollowed = false;
    let musicEnabled = false;
    let notificationsEnabled = false;
    let mobileOptimized = false;

    // Menú
    document.getElementById('menuBtn').addEventListener('click', () => {
      document.getElementById('menu').classList.add('active');
    });
    document.getElementById('closeMenu').addEventListener('click', () => {
      document.getElementById('menu').classList.remove('active');
    });

    // Mostrar modal de TikTok al cargar
    window.addEventListener('load', () => {
      setTimeout(() => {
        document.getElementById('modalTiktok').style.display = 'flex';
      }, 1000);
    });

    function closeModalTiktok() {
      document.getElementById('modalTiktok').style.display = 'none';
    }

    function closeModalError() {
      document.getElementById('modalError').style.display = 'none';
    }

    function seguirTikTok() {
      tikTokFollowed = true;
      setTimeout(() => {
        document.getElementById('modalTiktok').style.display = 'none';
      }, 1000);
    }

    function checkTikTokFollow() {
      if (tikTokFollowed) {
        generarLink();
      } else {
        document.getElementById('modalError').style.display = 'flex';
      }
    }

    // Idioma
    function setLang(lang) {
      currentLang = lang;
      if (lang === 'es') {
        document.getElementById('createTitle').textContent = '✨ Crea tu Detalle Virtual';
        document.getElementById('createSubtitle').textContent = 'Llena todo y genera tu link personalizado ❤️';
        document.getElementById('labelPara').textContent = '💌 Para: Nombre de tu amor';
        document.getElementById('labelDe').textContent = '👨‍❤️‍💋‍👨 De: Tu nombre';
        document.getElementById('labelMensaje').textContent = '✍️ Tu mensaje (usa saltos de línea)';
        document.getElementById('labelFuente').textContent = '🎨 Tipo de letra';
        document.getElementById('labelColor').textContent = '🌈 Color del texto';
        document.getElementById('labelCodigo').textContent = '🔐 Código de acceso (ej: 10/11/23)';
        document.getElementById('labelFoto').textContent = '🖼️ URL de foto principal';
        document.getElementById('labelGaleria').textContent = '🖼️ URLs de fotos para galería (una por línea)';
        document.getElementById('btnGenerar').textContent = 'Generar Link 🌟';
        document.getElementById('linkTitle').textContent = '🔗 Tu link está listo';
        document.getElementById('btnCopiar').textContent = '📋 Copiar Link';
        document.getElementById('btnWhatsApp').textContent = '💬 Enviar por WhatsApp';
      } else if (lang === 'en') {
        document.getElementById('createTitle').textContent = '✨ Create Your Detail';
        document.getElementById('createSubtitle').textContent = 'Fill everything and generate your link ❤️';
        document.getElementById('labelPara').textContent = '💌 For: Your love name';
        document.getElementById('labelDe').textContent = '👨‍❤️‍💋‍👨 From: Your name';
        document.getElementById('labelMensaje').textContent = '✍️ Your message (use line breaks)';
        document.getElementById('labelFuente').textContent = '🎨 Font style';
        document.getElementById('labelColor').textContent = '🌈 Text color';
        document.getElementById('labelCodigo').textContent = '🔐 Access code (e.g. 10/11/23)';
        document.getElementById('labelFoto').textContent = '🖼️ Main photo URL';
        document.getElementById('labelGaleria').textContent = '🖼️ Gallery photos URLs (one per line)';
        document.getElementById('btnGenerar').textContent = 'Generate Link 🌟';
        document.getElementById('linkTitle').textContent = '🔗 Your link is ready';
        document.getElementById('btnCopiar').textContent = '📋 Copy Link';
        document.getElementById('btnWhatsApp').textContent = '💬 Send via WhatsApp';
      } else if (lang === 'pt') {
        document.getElementById('createTitle').textContent = '✨ Crie seu Detalhe Virtual';
        document.getElementById('createSubtitle').textContent = 'Preencha tudo e gere seu link personalizado ❤️';
        document.getElementById('labelPara').textContent = '💌 Para: Nome do seu amor';
        document.getElementById('labelDe').textContent = '👨‍❤️‍💋‍👨 De: Seu nome';
        document.getElementById('labelMensaje').textContent = '✍️ Sua mensagem (use quebras de linha)';
        document.getElementById('labelFuente').textContent = '🎨 Estilo da fonte';
        document.getElementById('labelColor').textContent = '🌈 Cor do texto';
        document.getElementById('labelCodigo').textContent = '🔐 Código de acesso (ex: 10/11/23)';
        document.getElementById('labelFoto').textContent = '🖼️ URL da foto principal';
        document.getElementById('labelGaleria').textContent = '🖼️ URLs das fotos da galeria (uma por linha)';
        document.getElementById('btnGenerar').textContent = 'Gerar Link 🌟';
        document.getElementById('linkTitle').textContent = '🔗 Seu link está pronto';
        document.getElementById('btnCopiar').textContent = '📋 Copiar Link';
        document.getElementById('btnWhatsApp').textContent = '💬 Enviar pelo WhatsApp';
      }
    }

    // Tema
    function setTheme(theme) {
      currentTheme = theme;
      if (theme === 'dark') {
        document.body.classList.add('dark-mode');
      } else {
        document.body.classList.remove('dark-mode');
      }
    }

    // Generar link
    function generarLink() {
      const nombreElla = document.getElementById('nombreElla').value.trim();
      const nombreYo = document.getElementById('nombreYo').value.trim();
      const mensaje = document.getElementById('mensaje').value.trim();
      const codigoAcceso = document.getElementById('codigoAcceso').value.trim();
      const fotoPrincipal = document.getElementById('fotoPrincipal').value.trim() || 'https://via.placeholder.com/400x300?text=Foto+Principal';
      const fotosGaleria = document.getElementById('fotosGaleria').value.trim();
      const fuenteTexto = document.getElementById('fuenteTexto').value;
      const colorTexto = document.getElementById('colorTexto').value;

      if (!nombreElla || !nombreYo || !mensaje || !codigoAcceso) {
        alert(currentLang === 'es' ? 'Completa todos los campos.' : currentLang === 'en' ? 'Complete all fields.' : 'Preencha todos os campos.');
        return;
      }

      data = { nombreElla, nombreYo, mensaje, codigoAcceso, fotoPrincipal, fotosGaleria, fuenteTexto, colorTexto };
      const id = Math.random().toString(36).substr(2, 6);
      localStorage.setItem('detalle_' + id, JSON.stringify(data));

      const link = `${window.location.href.split('#')[0]}#${id}`;
      document.getElementById('linkInput').value = link;
      document.getElementById('linkBox').style.display = 'block';
      document.getElementById('linkBox').scrollIntoView({ behavior: 'smooth' });
    }

    function copyLink() {
      const link = document.getElementById('linkInput').value;
      navigator.clipboard.writeText(link).then(() => {
        alert(currentLang === 'es' ? '✅ Link copiado' : currentLang === 'en' ? '✅ Link copied' : '✅ Link copiado');
      });
    }

    function shareOnWhatsApp() {
      const link = document.getElementById('linkInput').value;
      const text = currentLang === 'es' ? `Hola mi amor, tengo un detalle especial para ti 💖\n\nHaz clic aquí: ${link}` :
                   currentLang === 'en' ? `Hello my love, I have a special detail for you 💖\n\nClick here: ${link}` :
                   `Olá meu amor, tenho um detalhe especial para você 💖\n\nClique aqui: ${link}`;
      window.open(`https://wa.me/?text=${encodeURIComponent(text)}`, '_blank');
    }

    // Pantalla de bloqueo
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
      letter.style.fontFamily = data.fuenteTexto;
      letter.style.color = data.colorTexto;
      letter.textContent = '';
      let i = 0;
      const speed = 40;
      function type() {
        if (i < data.mensaje.length) {
          letter.textContent += data.mensaje.charAt(i);
          i++;
          setTimeout(type, speed);
        }
      }
      setTimeout(type, 500);
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

    // Volver a personalizar
    function volverACrear() {
      document.getElementById('mainContainer').style.display = 'none';
      document.getElementById('createScreen').style.display = 'block';
      document.getElementById('linkBox').style.display = 'none';
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
          alert('❌ Detalle no encontrado.');
        }
      }
    });

    // Ajustes adicionales
    function toggleMusic() {
      musicEnabled = !musicEnabled;
      alert(musicEnabled ? '🎵 Música activada' : '🔇 Música desactivada');
    }

    function toggleNotifications() {
      notificationsEnabled = !notificationsEnabled;
      alert(notificationsEnabled ? '🔔 Notificaciones activadas' : '🔕 Notificaciones desactivadas');
    }

    function optimizeMobile() {
      mobileOptimized = !mobileOptimized;
      alert(mobileOptimized ? '📱 Modo móvil optimizado' : '🖥️ Modo normal');
    }
  </script>
</body>
</html>
