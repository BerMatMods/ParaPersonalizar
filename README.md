
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

    .glow-frame img, .glow-frame button, .glow-frame input {
      border-radius: 16px;
      display: block;
      width: 100%;
      border: 4px solid #fff;
    }

    /* Menú de tres rayas */
    .menu-btn {
      position: absolute;
      top: 20px;
      left: 20px;
      cursor: pointer;
      z-index: 100;
      width: 40px;
      height: 40px;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
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
      padding: 80px 20px 20px;
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

    /* Modales */
    .modal {
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

    .modal-content {
      background: var(--card-bg);
      border-radius: 20px;
      padding: 25px;
      max-width: 400px;
      width: 90%;
      text-align: center;
      box-shadow: 0 10px 40px rgba(0,0,0,0.2);
      border: var(--border);
      position: relative;
    }

    .modal-title {
      color: var(--primary);
      font-family: 'Playfair Display', serif;
      margin-bottom: 15px;
      font-size: 1.6em;
    }

    .modal-close {
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

    /* Botones en modales */
    .modal-btn {
      margin: 10px 5px;
      padding: 10px 18px;
      background: var(--primary);
      color: white;
      border: none;
      border-radius: 12px;
      cursor: pointer;
      font-size: 1em;
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

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
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

    /* Responsive */
    @media (max-width: 480px) {
      .create-screen, .link-box, .credit {
        padding: 1.4rem;
        max-width: 98%;
      }

      .link-actions {
        flex-direction: column;
      }

      button {
        width: 100%;
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
    <h3 class="menu-title">🔧 Menú</h3>
    <div class="menu-grid">
      <div class="menu-item" onclick="openModal('langModal')">🌐 Idioma</div>
      <div class="menu-item" onclick="openModal('themeModal')">🌙 Tema</div>
      <div class="menu-item" onclick="openModal('infoModal')">ℹ️ Información</div>
      <div class="menu-item" onclick="openModal('contactModal')">📞 Contacto</div>
    </div>
  </div>

  <!-- Modal: Idioma -->
  <div id="langModal" class="modal">
    <div class="modal-content">
      <div class="modal-close" onclick="closeModal('langModal')">×</div>
      <h3 class="modal-title">🌐 Idioma</h3>
      <p>Selecciona tu idioma:</p>
      <button class="modal-btn" onclick="setLang('es'); closeModal('langModal')">Español</button>
      <button class="modal-btn" onclick="setLang('en'); closeModal('langModal')">English</button>
    </div>
  </div>

  <!-- Modal: Tema -->
  <div id="themeModal" class="modal">
    <div class="modal-content">
      <div class="modal-close" onclick="closeModal('themeModal')">×</div>
      <h3 class="modal-title">🎨 Tema</h3>
      <p>Elige tu modo:</p>
      <button class="modal-btn" onclick="setTheme('light'); closeModal('themeModal')">Claro</button>
      <button class="modal-btn" onclick="setTheme('dark'); closeModal('themeModal')">Oscuro</button>
    </div>
  </div>

  <!-- Modal: Información -->
  <div id="infoModal" class="modal">
    <div class="modal-content">
      <div class="modal-close" onclick="closeModal('infoModal')">×</div>
      <h3 class="modal-title">ℹ️ Información</h3>
      <p style="color:var(--dark); text-align:left; margin:10px 0;">
        <strong>Software:</strong> Detalles Virtuales<br>
        <strong>Desarrollado por:</strong> AnthZz Berrocal _ BerMatMods<br>
        <strong>Versión:</strong> 1.0<br>
        <strong>Plataforma:</strong> Web (HTML/CSS/JS)<br><br>
        Creado con amor para hacer sentir especial a tu persona.
      </p>
      <button class="modal-btn" onclick="closeModal('infoModal')">Cerrar</button>
    </div>
  </div>

  <!-- Modal: Contacto -->
  <div id="contactModal" class="modal">
    <div class="modal-content">
      <div class="modal-close" onclick="closeModal('contactModal')">×</div>
      <h3 class="modal-title">📞 Contacto Directo</h3>
      <p style="color:var(--dark);">¿Quieres un detalle más personalizado o profesional?</p>
      <a href="https://wa.me/51937556459?text=Hola%20AnthZz,%20quiero%20un%20detalle%20personalizado" target="_blank" style="margin:15px auto; padding:12px 20px; background:var(--secondary); color:white; text-decoration:none; border-radius:12px; display:inline-block;">
        💬 Chatear por WhatsApp
      </a>
      <p style="font-size:0.9em; color:var(--primary); margin-top:10px;">+51 937 556 459</p>
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
        heart.style.position = 'fixed';
        heart.style.left = Math.random() * 90 + 5 + 'vw';
        heart.style.bottom = '0';
        heart.style.fontSize = '20px';
        heart.style.color = ['#e91e63', '#9c27b0'][Math.floor(Math.random()*2)];
        heart.style.pointerEvents = 'none';
        heart.style.zIndex = '1000';
        heart.style.opacity = '0';
        heart.style.animation = 'floatUp 18s ease-out forwards, fadeHeart 4s ease-in-out infinite';
        document.body.appendChild(heart);
        setTimeout(() => heart.remove(), 18000);
      }, 2500);
    }
    createHearts();
  </script>

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

    <button onclick="generarLink()"><span id="btnGenerar">Generar Link 🌟</span></button>

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

  <!-- Créditos -->
  <p class="credit">Desarrollado por AnthZz Berrocal | BerMatMods</p>

  <script>
    let input = '';
    let data = {};
    let currentLang = 'es';
    let currentTheme = 'light';

    // Menú
    document.getElementById('menuBtn').addEventListener('click', () => {
      document.getElementById('menu').classList.add('active');
    });
    document.getElementById('closeMenu').addEventListener('click', () => {
      document.getElementById('menu').classList.remove('active');
    });

    // Modales
    function openModal(id) {
      document.getElementById(id).style.display = 'flex';
      document.getElementById('menu').classList.remove('active');
    }

    function closeModal(id) {
      document.getElementById(id).style.display = 'none';
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
      } else {
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
        alert(currentLang === 'es' ? 'Completa todos los campos.' : 'Complete all fields.');
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
        alert(currentLang === 'es' ? '✅ Link copiado al portapapeles' : '✅ Link copied to clipboard');
      });
    }

    function shareOnWhatsApp() {
      const link = document.getElementById('linkInput').value;
      const text = currentLang === 'es'
        ? `Hola mi amor, tengo un detalle especial para ti 💖\n\nHaz clic aquí: ${link}`
        : `Hello my love, I have a special detail for you 💖\n\nClick here: ${link}`;
      window.open(`https://wa.me/?text=${encodeURIComponent(text)}`, '_blank');
    }

    // Cargar en hash
    window.addEventListener('load', () => {
      const hash = window.location.hash.slice(1);
      if (hash) {
        const saved = localStorage.getItem('detalle_' + hash);
        if (saved) {
          data = JSON.parse(saved);
          document.getElementById('createScreen').style.display = 'none';
          // Aquí iría la lógica de carta (se puede extender si deseas)
        }
      }
    });
  </script>
</body>
</html>
