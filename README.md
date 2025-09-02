
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

    /* Menú Hamburguesa - Ahora en la izquierda */
    .menu-toggle {
      position: fixed;
      top: 20px;
      left: 20px; /* Cambiado a la izquierda */
      width: 50px;
      height: 50px;
      background: var(--card-bg);
      border-radius: 50%;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      cursor: pointer;
      z-index: 1001;
      box-shadow: 0 6px 20px rgba(0,0,0,0.2);
      border: 3px solid transparent;
      animation: pulse 2s infinite alternate;
    }

    .menu-toggle span {
      display: block;
      width: 26px;
      height: 3px;
      background: var(--primary);
      margin: 3px 0;
      border-radius: 2px;
      transition: 0.3s;
    }

    .menu-toggle.active {
      border: 3px solid var(--primary);
      animation: rainbowGlow 2s ease-in-out infinite;
    }

    .menu-toggle.active span:nth-child(1) {
      transform: rotate(45deg) translate(6px, 6px);
    }

    .menu-toggle.active span:nth-child(2) {
      opacity: 0;
    }

    .menu-toggle.active span:nth-child(3) {
      transform: rotate(-45deg) translate(6px, -6px);
    }

    @keyframes pulse {
      0% { transform: scale(1); }
      100% { transform: scale(1.05); }
    }

    /* Menú desplegable - ahora desde la izquierda */
    .menu-panel {
      position: fixed;
      top: 0;
      left: -320px; /* Sale desde la izquierda */
      width: 300px;
      height: 100vh;
      background: var(--card-bg);
      box-shadow: 10px 0 30px rgba(0,0,0,0.15);
      border-right: var(--border);
      z-index: 1000;
      transition: left 0.5s cubic-bezier(0.68, -0.55, 0.265, 1.55);
      padding: 80px 20px 40px;
      display: flex;
      flex-direction: column;
      align-items: center;
      overflow-y: auto;
    }

    .menu-panel.active {
      left: 0;
      animation: slideIn 0.5s forwards;
    }

    @keyframes slideIn {
      from { transform: translateX(-100%); opacity: 0.8; }
      to { transform: translateX(0); opacity: 1; }
    }

    .menu-panel h3 {
      font-family: 'Playfair Display', serif;
      color: var(--primary);
      margin-bottom: 20px;
      font-size: 1.8rem;
      text-align: center;
    }

    .menu-profile {
      text-align: center;
      margin-bottom: 30px;
      padding: 20px;
      background: rgba(156, 39, 176, 0.08);
      border-radius: 16px;
      width: 100%;
      border: 2px dashed var(--primary);
    }

    .menu-profile h4 {
      color: var(--primary);
      font-size: 1.4rem;
      margin-bottom: 8px;
    }

    .menu-profile p {
      color: var(--dark);
      font-size: 0.95rem;
    }

    .menu-btn {
      display: block;
      width: 100%;
      padding: 14px 20px;
      margin: 10px 0;
      background: linear-gradient(45deg, var(--primary), var(--secondary));
      color: white;
      border: none;
      border-radius: 14px;
      font-size: 1.1rem;
      font-weight: 600;
      cursor: pointer;
      text-align: center;
      box-shadow: var(--border-glow);
      transition: all 0.3s;
    }

    .menu-btn:hover {
      transform: translateY(-3px);
      box-shadow: 0 10px 25px rgba(156, 39, 176, 0.5);
    }

    .menu-close {
      position: absolute;
      top: 20px;
      left: 20px;
      font-size: 1.8rem;
      color: var(--primary);
      cursor: pointer;
      background: #fff;
      width: 40px;
      height: 40px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
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

      .menu-toggle {
        top: 15px;
        left: 15px;
        width: 45px;
        height: 45px;
      }

      .menu-toggle span {
        width: 22px;
        height: 2.5px;
      }

      .menu-panel {
        width: 280px;
      }

      .menu-panel h3 {
        font-size: 1.6rem;
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

  <!-- Menú Hamburguesa - Ahora en la parte superior izquierda -->
  <div class="menu-toggle" id="menuToggle">
    <span></span>
    <span></span>
    <span></span>
  </div>

  <div class="menu-panel" id="menuPanel">
    <div class="menu-close" onclick="closeMenu()">×</div>
    <h3>✨ Menú BerMatMods</h3>

    <div class="menu-profile">
      <h4>AnthZz Berrocal</h4>
      <p>Desarrollador | BerMatMods</p>
      <p>Detalles virtuales únicos y románticos</p>
    </div>

    <!-- Nuevas opciones con efectos -->
    <button class="menu-btn glow-frame" onclick="toggleDarkMode()">
      🌙 Modo Oscuro
    </button>

    <button class="menu-btn glow-frame" onclick="toggleMusic()">
      🎵 Música de Fondo <span id="musicStatus">▶️</span>
    </button>

    <a href="https://wa.me/937556459?text=Hola%20AnthZz,%20me%20encantó%20tu%20proyecto%20de%20detalles%20virtuales.%20¿Puedo%20encargarte%20uno?" target="_blank" class="menu-btn glow-frame">
      📞 Consulta Personalizada
    </a>

    <button class="menu-btn glow-frame" onclick="shareProject()">
      📱 Compartir Proyecto
    </button>

    <button class="menu-btn glow-frame" onclick="aboutProject()">
      🧾 Acerca del Proyecto
    </button>

    <button class="menu-btn glow-frame" onclick="location.reload()">
      🔄 Recargar
    </button>
  </div>

  <!-- Modal: Requisito TikTok -->
  <div id="modalTiktok" class="modal-tiktok">
    <div class="modal-tiktok-content">
      <div class="modal-tiktok-close" onclick="closeModalTiktok()">×</div>
      <h3 class="modal-tiktok-title">🔔 ¡Importante!</h3>
      <p style="color:var(--dark); margin:10px 0;">
        Para crear tu detalle personalizado, primero debes seguir a mi cuenta de TikTok.
      </p>
      <a href="https://www.tiktok.com/@bermat_mods?_t=ZS-8zNy5TzEpoi&_r=1" target="_blank" class="btn-tiktok" onclick="seguirTikTok()">
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
        El sistema de <strong>BerMatMods</strong> ha detectado que no has hecho clic en "Seguir en TikTok".
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
      <input type="url" id="fotoPrincipal" placeholder=" https://ejemplo.com/foto.jpg " />
    </div>

    <div class="form-group">
      <label id="labelGaleria">🖼️ URLs de fotos para galería (una por línea)</label>
      <textarea id="fotosGaleria" placeholder="https://ejemplo.com/foto1.jpg 
https://ejemplo.com/foto2.jpg "></textarea>
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
      <img src="https://media2.giphy.com/media/v1.Y2lkPTZjMDliOTUyZTAxbHV0Mm1rYmI2emc3ZmdvcGdka2szMGMzMHl4ZXlhcmEzN3A4cCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/Y62ofc4S1Vst2/giphy.gif " alt="Corazones flotando" />
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
      <img src="https://media0.giphy.com/media/v1.Y2lkPTZjMDliOTUyMzl0NTh2ZHhmOHF1Nm45NHNqcmN1bTVrdHNtbDgwbjZpZTFqMno3diZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/11TyfGbDbBv4be/giphy.gif " alt="Bailarina de amor" />
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

  <script>
    let input = '';
    let data = {};

    // Verificar si ya hizo clic en "Seguir"
    window.addEventListener('load', () => {
      const yaSigue = localStorage.getItem('tiktokFollowed') === 'true';
      
      if (!yaSigue) {
        setTimeout(() => {
          document.getElementById('modalTiktok').style.display = 'flex';
        }, 1000);
      }
    });

    function closeModalTiktok() {
      document.getElementById('modalTiktok').style.display = 'none';
    }

    function closeModalError() {
      document.getElementById('modalError').style.display = 'none';
    }

    function seguirTikTok() {
      localStorage.setItem('tiktokFollowed', 'true');
    }

    function checkTikTokFollow() {
      const yaSigue = localStorage.getItem('tiktokFollowed') === 'true';
      if (yaSigue) {
        generarLink();
      } else {
        document.getElementById('modalError').style.display = 'flex';
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
        alert('Completa todos los campos.');
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
        alert('✅ Link copiado');
      });
    }

    function shareOnWhatsApp() {
      const link = document.getElementById('linkInput').value;
      const text = `Hola mi amor, tengo un detalle especial para ti 💖\n\nHaz clic aquí: ${link}`;
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

    // === FUNCIONES DEL MENÚ ===
    const menuToggle = document.getElementById('menuToggle');
    const menuPanel = document.getElementById('menuPanel');

    menuToggle.addEventListener('click', () => {
      menuToggle.classList.toggle('active');
      menuPanel.classList.toggle('active');
    });

    function closeMenu() {
      menuToggle.classList.remove('active');
      menuPanel.classList.remove('active');
    }

    // Modo oscuro
    function toggleDarkMode() {
      document.body.classList.toggle('dark-mode');
      localStorage.setItem('darkMode', document.body.classList.contains('dark-mode'));
    }

    // Música de fondo
    const audio = new Audio('https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3'); // Música de ejemplo suave
    audio.loop = true;
    let isPlaying = false;

    function toggleMusic() {
      const btn = document.getElementById('musicStatus');
      if (isPlaying) {
        audio.pause();
        btn.textContent = '▶️';
      } else {
        audio.play().catch(e => alert('Permite audio para activar la música.'));
        btn.textContent = '⏸️';
      }
      isPlaying = !isPlaying;
    }

    // Compartir proyecto
    function shareProject() {
      const text = "Mira este increíble detalle virtual que encontré 💖\n\nPuedes crear uno personalizado aquí: " + window.location.href;
      if (navigator.share) {
        navigator.share({ text });
      } else {
        navigator.clipboard.writeText(text).then(() => {
          alert('Enlace copiado para compartir 📲');
        });
      }
    }

    // Acerca del proyecto
    function aboutProject() {
      alert(`✨ Detalles Virtuales v1.0\n\nCreado por: AnthZz Berrocal\nMarca: BerMatMods\n\nUn proyecto romántico y personalizado para expresar amor de forma digital.\n\n© 2025 BerMatMods`);
    }
  </script>
</body>
</html>
