
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Detalles Virtuales ❤️</title>

  <!-- Google Fonts: Letras bonitas -->
  <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Quicksand:wght@500;600&family=Pacifico&display=swap" rel="stylesheet">

  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      background: linear-gradient(135deg, #f9f4f5, #e0d4e3);
      min-height: 100vh;
      font-family: 'Quicksand', sans-serif;
      color: #5d3a5d;
      overflow-x: hidden;
      position: relative;
      transition: background 0.5s ease;
    }

    /* Fondo con GIFs suaves */
    .gif-bg {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: 0;
      opacity: 0.2;
    }

    .gif-bg img {
      position: absolute;
      width: 80px;
      height: 80px;
      border-radius: 50%;
      filter: drop-shadow(0 0 5px rgba(255,105,180,0.3));
      animation: float 8s ease-in-out infinite, rotate 15s linear infinite;
    }

    @keyframes float {
      0%, 100% { transform: translateY(0) translateX(0); }
      50% { transform: translateY(-25px) translateX(10px); }
    }

    @keyframes rotate {
      0% { opacity: 0.6; }
      50% { opacity: 0.3; }
      100% { opacity: 0.6; }
    }

    /* Contenedor principal con efecto vidrio */
    .container {
      max-width: 95%;
      margin: 30px auto;
      padding: 25px;
      background: rgba(255, 255, 255, 0.35);
      backdrop-filter: blur(12px);
      border-radius: 22px;
      box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
      z-index: 2;
      position: relative;
      border: 1px solid rgba(255, 105, 180, 0.3);
      max-width: 500px;
    }

    .container::before {
      content: '';
      position: absolute;
      inset: -2px;
      background: linear-gradient(45deg, #ff9a9e, #fad0c4, #ff9a9e);
      z-index: -1;
      border-radius: 24px;
      opacity: 0;
      transition: opacity 0.4s;
    }

    .container:hover::before {
      opacity: 1;
    }

    h1 {
      text-align: center;
      font-family: 'Pacifico', cursive;
      font-size: 2.4em;
      color: #d64161;
      margin-bottom: 15px;
      text-shadow: 1px 1px 3px rgba(0,0,0,0.1);
    }

    p.subtitle {
      text-align: center;
      font-size: 1.1em;
      color: #885a80;
      margin-bottom: 25px;
    }

    /* Menú hamburguesa */
    .menu-btn {
      position: absolute;
      top: 20px;
      left: 20px;
      cursor: pointer;
      z-index: 10;
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
      background: #d64161;
      border-radius: 2px;
      transition: 0.3s;
    }

    .menu {
      position: fixed;
      top: 0;
      left: -300px;
      width: 280px;
      height: 100vh;
      background: linear-gradient(to bottom, #7b4397, #dc2430);
      transition: left 0.4s ease;
      z-index: 100;
      padding: 60px 20px 20px;
      box-shadow: 5px 0 20px rgba(0,0,0,0.3);
    }

    .menu.active {
      left: 0;
    }

    .menu ul {
      list-style: none;
    }

    .menu ul li {
      margin: 22px 0;
    }

    .menu ul li a {
      color: #fff;
      text-decoration: none;
      font-size: 1.2em;
      font-weight: 500;
      display: flex;
      align-items: center;
    }

    .menu ul li a::before {
      content: "✨";
      margin-right: 10px;
    }

    .close-btn {
      position: absolute;
      top: 20px;
      right: 20px;
      font-size: 1.8em;
      color: white;
      cursor: pointer;
    }

    /* Formulario */
    .form-group {
      margin-bottom: 18px;
    }

    label {
      display: block;
      margin-bottom: 8px;
      color: #9c27b0;
      font-weight: 600;
      font-size: 0.95em;
    }

    input, textarea, select {
      width: 100%;
      padding: 12px 14px;
      border: 1px solid #e1bee7;
      border-radius: 14px;
      font-size: 1em;
      background: rgba(255, 255, 255, 0.7);
      backdrop-filter: blur(5px);
      color: #4a148c;
      transition: all 0.3s;
      font-family: inherit;
    }

    input:focus, textarea:focus, select:focus {
      outline: none;
      border-color: #9c27b0;
      box-shadow: 0 0 0 2px rgba(156, 39, 176, 0.2);
    }

    button {
      background: linear-gradient(45deg, #9c27b0, #e91e63);
      color: white;
      border: none;
      padding: 14px;
      border-radius: 15px;
      font-size: 1.1em;
      cursor: pointer;
      width: 100%;
      margin-top: 10px;
      box-shadow: 0 5px 15px rgba(156, 39, 176, 0.3);
      transition: transform 0.2s, box-shadow 0.2s;
      font-weight: 600;
    }

    button:hover {
      transform: translateY(-2px);
      box-shadow: 0 8px 20px rgba(156, 39, 176, 0.4);
    }

    /* Vista del detalle */
    .detail-view {
      display: none;
      text-align: center;
      padding: 25px 15px;
      background: rgba(255, 255, 255, 0.4);
      border-radius: 20px;
      margin-top: 20px;
      box-shadow: 0 5px 20px rgba(0,0,0,0.1);
    }

    .detail-view h2 {
      font-family: 'Dancing Script', cursive;
      font-size: 2.2em;
      color: #9c27b0;
      margin-bottom: 15px;
    }

    .detail-card {
      display: inline-block;
      padding: 25px;
      margin: 15px auto;
      max-width: 90%;
      min-height: 180px;
      border-radius: 20px;
      box-shadow: 0 5px 25px rgba(0,0,0,0.1);
      position: relative;
      overflow: hidden;
      transition: all 0.3s;
    }

    .detail-card::before {
      content: '';
      position: absolute;
      inset: 0;
      background: radial-gradient(circle, rgba(255,255,255,0.6) 0%, rgba(255,255,255,0.2) 70%);
      z-index: 1;
    }

    .detail-card p {
      position: relative;
      z-index: 2;
      font-size: 1.2em;
      line-height: 1.7;
      color: #444;
    }

    .detail-view .sender {
      font-family: 'Dancing Script', cursive;
      font-size: 1.4em;
      color: #e91e63;
      margin-top: 15px;
      font-weight: bold;
    }

    .action-btns {
      margin-top: 20px;
      display: flex;
      flex-direction: column;
      gap: 10px;
    }

    .copy-link, .share-whatsapp {
      padding: 12px;
      border-radius: 12px;
      font-size: 1em;
      cursor: pointer;
    }

    .copy-link {
      background: #4a148c;
    }

    .share-whatsapp {
      background: #25D366;
    }

    .back-btn {
      background: #757575;
      margin-top: 15px;
    }

    .footer {
      text-align: center;
      padding: 25px;
      color: #7b4397;
      font-size: 0.95em;
      margin-top: 20px;
      z-index: 2;
      position: relative;
    }

    .footer strong {
      color: #9c27b0;
      font-weight: 600;
    }
  </style>
</head>
<body>

  <!-- Fondo con GIFs tiernos -->
  <div class="gif-bg" id="gifContainer"></div>

  <!-- Menú de hamburguesa -->
  <div class="menu-btn" id="menuBtn">
    <span></span>
    <span></span>
    <span></span>
  </div>

  <div class="menu" id="menu">
    <div class="close-btn" id="closeMenu">&times;</div>
    <ul>
      <li><a href="#" onclick="showForm()">Crear Detalle 💖</a></li>
      <li><a href="#" onclick="showHow()">¿Cómo funciona? ℹ️</a></li>
      <li><a href="#">Créditos: AnthZz Berrocal ✨</a></li>
    </ul>
  </div>

  <div class="container" id="mainContainer">
    <h1>Detalles Virtuales</h1>
    <p class="subtitle">Hazle sentir único con una carta personalizada</p>

    <!-- Formulario -->
    <div id="formSection">
      <div class="form-group">
        <label>💌 Nombre de tu amor</label>
        <input type="text" id="name" placeholder="Ej: Sofía" />
      </div>
      <div class="form-group">
        <label>👨‍❤️‍💋‍👨 Tu nombre</label>
        <input type="text" id="sender" placeholder="Ej: Andrés" />
      </div>
      <div class="form-group">
        <label>✍️ Tu mensaje o carta</label>
        <textarea id="message" rows="6" placeholder="Escribe palabras del corazón..."></textarea>
      </div>

      <div class="form-group">
        <label>🎨 Fondo de la carta</label>
        <select id="cardBg">
          <option value="linear-gradient(135deg, #fff8f8, #ffebee)">Rosa suave</option>
          <option value="linear-gradient(135deg, #f3e5f5, #ede7f6)">Lavanda</option>
          <option value="linear-gradient(135deg, #e8f5e8, #c8e6c9)">Verde pastel</option>
          <option value="white">Blanco clásico</option>
          <option value="url('https://www.transparenttextures.com/patterns/speckle-dark.png')">Textura sutil</option>
        </select>
      </div>

      <div class="form-group">
        <label>🖋️ Tipo de letra</label>
        <select id="fontFamily">
          <option value="'Quicksand', sans-serif">Moderna (Quicksand)</option>
          <option value="'Dancing Script', cursive">Elegante (Script)</option>
          <option value="'Pacifico', cursive">Divertida (Pacifico)</option>
          <option value="Arial, sans-serif">Simple (Arial)</option>
        </select>
      </div>

      <div class="form-group">
        <label>📏 Tamaño del texto</label>
        <select id="fontSize">
          <option value="1.1em">Pequeño</option>
          <option value="1.3em" selected>Mediano</option>
          <option value="1.5em">Grande</option>
          <option value="1.7em">Muy grande</option>
        </select>
      </div>

      <div class="form-group">
        <label>🌈 Color del texto</label>
        <select id="textColor">
          <option value="#444">Gris oscuro</option>
          <option value="#5d3a5d">Morado suave</option>
          <option value="#8B0000">Rojo amor</option>
          <option value="#006400">Verde esperanza</option>
          <option value="#000080">Azul profundo</option>
        </select>
      </div>

      <button onclick="generateLink()">Crear Mi Detalle 🌟</button>
    </div>

    <!-- Vista del detalle generado -->
    <div class="detail-view" id="detailView"></div>
  </div>

  <div class="footer">
    <strong>by AnthZz Berrocal BerMatMods</strong> ❤️ Hecho con amor y código
  </div>

  <script>
    // Lista de GIFs tiernos (Stitch, corazones, etc.)
    const gifs = [
      'https://media.tenor.com/05jMm-YVlKoAAAAC/stitch-hello.gif',
      'https://media.tenor.com/l6YwEaQyoaUAAAAC/stitch-love.gif',
      'https://media.tenor.com/5KbMYAkO6YUAAAAC/stitch-kiss.gif',
      'https://media.tenor.com/9xDT_fIyGdIAAAAC/love-stitch.gif',
      'https://media.tenor.com/8ZnMk6sVx6cAAAAC/stitch-heart.gif',
      'https://i.giphy.com/media/v1.Y2lkPTc5MGI3NjExeXVnN3N2dG55Y2Z6NzR3c292bGZ1Y250cGw2ZmZ5ZmN6a2Z5Z3d1dyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/3o7TKsQ8UQ4l4LhG2U/giphy.gif',
      'https://i.giphy.com/media/v1.Y2lkPTc5MGI3NjExaWZpN3N6aG54Ym91ZjR5cWx5d3B2d2x4aGx0Z2N5bWZ4ZGZ5b252NyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/26BRv0Thfl7iNRgoY/giphy.gif',
      'https://i.giphy.com/media/v1.Y2lkPTc5MGI3NjExNHJ2NnF5N2J0Z3B6N2R4M3V4Z3B5a3N5dG55dW91dGZ6ZjR6Y3l2dyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/l0HlRnHV7QH6kKfBa/giphy.gif',
      'https://media.tenor.com/XvU9r84P66QAAAAC/stitch-cute.gif',
      'https://media.tenor.com/6Z8vZ7uL1YIAAAAC/stitch-happy.gif'
    ];

    // Posiciones aleatorias
    const positions = [
      '10% 10%', '30% 5%', '60% 10%', '85% 15%',
      '15% 40%', '50% 35%', '80% 45%',
      '10% 70%', '40% 75%', '75% 70%'
    ];

    const gifContainer = document.getElementById('gifContainer');
    gifs.forEach((src, i) => {
      const img = document.createElement('img');
      img.src = src;
      const pos = positions[i] || `${Math.random()*90}% ${Math.random()*90}%`;
      img.style.left = pos.split(' ')[0];
      img.style.top = pos.split(' ')[1];
      img.style.transform = 'translate(-50%, -50%)';
      gifContainer.appendChild(img);
    });

    // Menú
    const menuBtn = document.getElementById('menuBtn');
    const closeMenu = document.getElementById('closeMenu');
    const menu = document.getElementById('menu');

    menuBtn.addEventListener('click', () => menu.classList.add('active'));
    closeMenu.addEventListener('click', () => menu.classList.remove('active'));

    // Mostrar formulario
    function showForm() {
      document.getElementById('formSection').style.display = 'block';
      document.getElementById('detailView').style.display = 'none';
      menu.classList.remove('active');
      window.location.hash = '';
    }

    function showHow() {
      alert("1. Llena todos los campos.\n2. Personaliza colores, letra y fondo.\n3. Haz clic en 'Crear Mi Detalle'.\n4. Se genera un link que puedes copiar o compartir por WhatsApp.\n5. Cuando tu amor lo abra, verá tu carta con todo el amor que le tienes 💖");
      menu.classList.remove('active');
    }

    // Generar link y guardar datos
    function generateLink() {
      const name = document.getElementById('name').value.trim();
      const sender = document.getElementById('sender').value.trim();
      const message = document.getElementById('message').value.trim();
      const cardBg = document.getElementById('cardBg').value;
      const fontFamily = document.getElementById('fontFamily').value;
      const fontSize = document.getElementById('fontSize').value;
      const textColor = document.getElementById('textColor').value;

      if (!name || !sender || !message) {
        alert('⚠️ Por favor, completa todos los campos.');
        return;
      }

      const data = { name, sender, message, cardBg, fontFamily, fontSize, textColor };
      const id = Math.random().toString(36).substr(2, 6);
      localStorage.setItem('detail_' + id, JSON.stringify(data));

      const link = `${window.location.href.split('#')[0]}#${id}`;
      showDetailView(data, link);
      window.location.hash = id;
    }

    // Mostrar el detalle
    function showDetailView(data, link) {
      document.getElementById('formSection').style.display = 'none';
      const detailView = document.getElementById('detailView');

      detailView.innerHTML = `
        <h2>💌 Para: ${data.name}</h2>
        <div class="detail-card" style="background: ${data.cardBg};">
          <p style="font-family: ${data.fontFamily}; font-size: ${data.fontSize}; color: ${data.textColor};">
            ${data.message.replace(/\n/g, '<br>')}
          </p>
        </div>
        <p class="sender">Con todo mi amor, ${data.sender} 💞</p>
        <div class="action-btns">
          <button class="copy-link" onclick="copyLink('${link}')">📋 Copiar Link</button>
          <button class="share-whatsapp" onclick="shareOnWhatsApp('${encodeURIComponent(data.sender + ' te envió un detalle especial 💖')}', '${encodeURIComponent(link)}')">
            💬 Compartir por WhatsApp
          </button>
        </div>
        <button class="back-btn" onclick="showForm()">🔄 Crear otro detalle</button>
      `;
      detailView.style.display = 'block';
    }

    // Copiar link
    function copyLink(link) {
      navigator.clipboard.writeText(link).then(() => {
        alert('✅ Link copiado:\n\n' + link + '\n\nPuedes pegarlo y enviarlo por mensaje.');
      }).catch(() => {
        prompt('Link:', link);
      });
    }

    // Compartir en WhatsApp
    function shareOnWhatsApp(text, link) {
      const waUrl = `https://wa.me/?text=${text}%20-%20${link}`;
      window.open(waUrl, '_blank');
    }

    // Cargar detalle si hay hash
    window.addEventListener('load', () => {
      const hash = window.location.hash.slice(1);
      if (hash) {
        const data = JSON.parse(localStorage.getItem('detail_' + hash));
        if (data) {
          const link = `${window.location.href.split('#')[0]}#${hash}`;
          showDetailView(data, link);
        } else {
          alert('❌ Detalle no encontrado. Puede que haya sido eliminado.');
          showForm();
        }
      }
    });
  </script>
</body>
</html>
