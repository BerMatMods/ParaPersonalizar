<!DOCTYPE html><html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>⚡BerMat-Bot MD🔥</title>
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500&family=Share+Tech+Mono&display=swap" rel="stylesheet">
  <style>
    body {
      background: #000000;
      color: #00ffee;
      font-family: 'Share Tech Mono', monospace;
      margin: 0;
      padding: 0;
      background-image: url('https://i.ibb.co/ZMx6hC3/matrix-bg.gif');
      background-size: cover;
      background-attachment: fixed;
    }
    .container {
      max-width: 700px;
      margin: 50px auto;
      padding: 25px;
      background: rgba(10, 10, 10, 0.92);
      box-shadow: 0 0 35px #0ff;
      border-radius: 20px;
      animation: neonPulse 4s infinite ease-in-out;
    }
    @keyframes neonPulse {
      0%, 100% { box-shadow: 0 0 35px #00ffee; }
      50% { box-shadow: 0 0 60px #0ff, 0 0 20px #0ff inset; }
    }
    h1 {
      text-align: center;
      font-family: 'Orbitron', sans-serif;
      font-size: 2.8em;
      color: #00ffee;
      text-shadow: 0 0 15px #00ffee;
    }
    .chat-box {
      background: #111;
      border-radius: 15px;
      padding: 15px;
      height: 500px;
      overflow-y: auto;
      box-shadow: inset 0 0 15px #00ffcc44;
      font-size: 1.1em;
    }
    .user, .bot {
      padding: 12px 16px;
      margin: 12px;
      border-radius: 14px;
      max-width: 90%;
      animation: fadeIn 0.4s ease;
    }
    .user {
      background: #0047ab;
      color: #fff;
      align-self: flex-end;
      margin-left: auto;
      font-weight: bold;
    }
    .bot {
      background: #0c0c0c;
      color: #00ffee;
      border-left: 4px solid #00ffee;
      font-family: 'Courier New', Courier, monospace;
    }
    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }
    input {
      width: 100%;
      padding: 14px;
      border-radius: 12px;
      border: none;
      margin-top: 20px;
      background: #000;
      color: #0ff;
      font-size: 1em;
      font-family: 'Share Tech Mono', monospace;
      box-shadow: 0 0 10px #0ff;
    }
    .footer {
      text-align: center;
      margin-top: 25px;
      color: #ccc;
      font-size: 0.9em;
    }
    .footer a {
      color: #00ffee;
      text-decoration: none;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>⚡BERMAT-BOT MD🔥</h1>
    <div class="chat-box" id="chat">
      <div class="bot">👾 Bienvenido a <b>⚡BERMAT-BOT MD🔥</b><br>Inteligencia Artificial Avanzada creada por <b>Anth'Zz Berrocal</b><br>Escribe comandos como <code>.Menu</code>, <code>.Info</code>, <code>.Hack</code>, <code>.Darkweb</code>, <code>.Verso</code>...</div>
    </div>
    <input type="text" id="userInput" placeholder="🔐 Escribe un comando aquí y presiona Enter..." onkeydown="if(event.key==='Enter'){sendMessage()}" />
    <div class="footer">
      © 2025 por <strong>Anth'Zz Berrocal</strong> | Alias: <code>BerMatModZ</code> | Andahuaylas - Perú 🌐
    </div>
  </div>  <script>
    const chat = document.getElementById("chat");
    const responses = {
      ".menu": "📜 Comandos disponibles:<br>- .Info<br>- .Hack<br>- .Darkweb<br>- .Verso<br>- .Sticker<br>- .XO<br>- .Ayuda<br>- .Novia<br>- .Sistema<br>- .Creditos",
      ".info": "📌 Creador: Anth'Zz Berrocal<br>⚙️ Alias: BerMatModZ<br>🌍 Ciudad: Andahuaylas, Perú<br>📞 WhatsApp: 937556459<br>💻 Proyectos: ⚡BerMat-Bot MD🔥, Simulador Hacker, Web Interactiva<br>🎓 Habilidades: Python, Hacking Ético, IA, Termux, GitHub, Diseño Web Avanzado",
      ".hack": "🛠️ Simulando ataque...<br>🔗 Conectando al servidor<br>⚡ Inyección de paquetes...<br>💣 Sistema vulnerado con éxito - Nivel ROOT activo<br><em>Mensajes extraídos: 'AnthZz pásame el nuevo bot'...</em>",
      ".darkweb": "🌐 Accediendo al nodo encriptado de la DarkWeb...<br>Usuario: BerMatModZ | Estado: ACEPTADO<br>Bienvenido al subsistema clandestino de bots y exploits 💀",
      ".verso": "📝 'Cada línea de código, un poema cifrado,<br>en mi núcleo binario, tu nombre está programado' 💘 - Para Briyidth Jhorgina",
      ".xo": "🎮 Tres en Raya en marcha:<br>[❌ | 🟢 | ⬜]<br>[⬜ | ❌ | ⬜]<br>[⬜ | ⬜ | 🟢]",
      ".sticker": "🎨 Generando sticker .BerMat personalizado con código QR 💾... ¡Listo para descargar!",
      ".Chupapinga": "💖 Te amo muchísimo mi reina Briyidth Jhorgina 💘 Eres mi mundo y mi código más valioso 💌",
      ".sistema": "💻 Sistema Interno: BerMatOS AI Core v1.8<br>🔐 Seguridad: Criptografía cuántica<br>🧠 Motor de decisiones: GPT-BerMat Fusion<br>🧬 Estado: Estable y activo 24/7",
      ".ayuda": "🤖 Usa el comando .Menu para ver todo lo que puedes hacer. Este bot está potenciado por IA desarrollada por BerMatModZ.",
      ".creditos": "✨ Desarrollo por Anth'Zz Berrocal (BerMatModZ)<br>🛠️ Inspirado en la fuerza hacker peruana 🇵🇪<br>💾 Powered by Termux + HTML + JS + 💡 creatividad sin límites"
    };

    function sendMessage() {
      const input = document.getElementById("userInput");
      const text = input.value.trim();
      if (!text) return;

      const userMsg = document.createElement("div");
      userMsg.className = "user";
      userMsg.textContent = text;
      chat.appendChild(userMsg);

      const botMsg = document.createElement("div");
      botMsg.className = "bot";
      const response = responses[text.toLowerCase()] || "⚠️ Comando no reconocido. Escribe <code>.Menu</code> para ver las opciones disponibles.";
      botMsg.innerHTML = response;
      chat.appendChild(botMsg);

      chat.scrollTop = chat.scrollHeight;
      input.value = "";
    }
  </script></body>
</html>
