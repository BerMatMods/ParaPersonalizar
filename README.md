<!DOCTYPE html><html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>⚡BerMat-Bot MD🔥</title>
  <style>
    body {
      background: #0a0a0a;
      color: #e0e0e0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      margin: 0;
      padding: 0;
      background-image: url('https://i.ibb.co/ZMx6hC3/matrix-bg.gif');
      background-size: cover;
      background-attachment: fixed;
    }
    .container {
      max-width: 480px;
      margin: 40px auto;
      padding: 20px;
      background: rgba(0, 0, 0, 0.85);
      box-shadow: 0 0 20px #00ffcc;
      border-radius: 15px;
      animation: pulse 3s infinite;
    }
    @keyframes pulse {
      0%, 100% { box-shadow: 0 0 20px #00ffcc; }
      50% { box-shadow: 0 0 40px #00ffaa; }
    }
    h1 {
      text-align: center;
      color: #00ffcc;
      font-size: 2em;
      text-shadow: 0 0 10px #00ffcc;
    }
    .chat-box {
      background: #111;
      border-radius: 10px;
      padding: 10px;
      height: 400px;
      overflow-y: auto;
      box-shadow: inset 0 0 10px #00ffcc44;
    }
    .user, .bot {
      padding: 10px 14px;
      margin: 10px;
      border-radius: 12px;
      max-width: 80%;
      animation: fadeIn 0.5s ease;
    }
    .user {
      background: #005eff;
      align-self: flex-end;
      color: #fff;
      margin-left: auto;
    }
    .bot {
      background: #222;
      color: #00ffcc;
      border: 1px solid #00ffcc33;
      font-family: 'Courier New', Courier, monospace;
    }
    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }
    input {
      width: 100%;
      padding: 14px;
      border-radius: 10px;
      border: none;
      margin-top: 15px;
      background: #111;
      color: #00ffcc;
      outline: none;
      box-shadow: 0 0 10px #00ffcc33;
    }
    .footer {
      text-align: center;
      margin-top: 20px;
      color: #888;
      font-size: 0.85em;
    }
    .footer a {
      color: #00ffcc;
      text-decoration: none;
    }
    .footer a:hover {
      text-decoration: underline;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>⚡BerMat-Bot MD🔥</h1>
    <div class="chat-box" id="chat">
      <div class="bot">👋 Bienvenido al sistema BerMatModZ AI.<br>
        Yo soy <strong>⚡BerMat-Bot MD🔥</strong>, inteligencia artificial desarrollada por <strong>Anth'Zz Berrocal</strong>, también conocido como <code>BerMatModZ</code>.<br>
        Ingresa comandos como: <code>.BerMat hack</code>, <code>.BerMat sistema</code>, <code>.BerMat codename</code>, <code>.BerMat darkweb</code>
      </div>
    </div>
    <input type="text" id="userInput" placeholder="Escribe un comando de inteligencia o hackeo..." onkeydown="if(event.key==='Enter'){sendMessage()}" />
    <div class="footer">
      👾 Proyecto creado por <strong>Anth'Zz Berrocal</strong><br>
      🌐 Alias: <code>BerMatModZ</code> | 🧠 Especialista en Ciberseguridad & IA<br>
      📍 Desde Andahuaylas | 💬 WhatsApp: 937556459
    </div>
  </div>  <script>
    const chat = document.getElementById("chat");
    const responses = {
      ".bermat menu": "📜 Comandos disponibles:<br>- .BerMat novia<br>- .BerMat hack<br>- .BerMat sticker<br>- .BerMat xo<br>- .BerMat verso<br>- .BerMat sistema<br>- .BerMat info<br>- .BerMat darkweb<br>- .BerMat ayuda",
      ".bermat novia": "💖 Te amo muchísimo mi reina Briyidth Jhorgina 💘 Eres lo más valioso que tengo 💌",
      ".bermat hack": "🛠️ Iniciando proceso simulado de intrusión...<br>Estableciendo conexión 💻<br>Inyectando payload 📡<br><strong>Acceso permitido ✅</strong><br>Recopilando mensajes...<br><em>\"Tío Anth, pásame el bot pe que sea potente.\"</em>",
      ".bermat darkweb": "🌐 Conectando al nodo oculto...<br>📍 Localización cifrada: PERU NODE 51<br>🔐 Acceso como BerMatModZ | Nivel: Root<br>💀 Bienvenido al lado oscuro del código...",
      ".bermat sistema": "📊 Sistema Operativo: BerMatOS v1.0<br>🧠 Núcleo AI: GPT-BerMatCore<br>🔐 Seguridad: Nivel Militar<br>👤 Usuario Root: Anth'Zz Berrocal aka BerMatModZ",
      ".bermat sticker": "🎨 Generando sticker personalizado con firma BerMatModZ... ¡Exportado!",
      ".bermat xo": "🎮 Tres en Raya activado<br>[  ❌ | 🟢 | ⬜ ]<br>[  ⬜ | 🟢 | ⬜ ]<br>[  ⬜ | ⬜ | ❌ ]",
      ".bermat info": "📌 Perfil del Creador:<br>👤 Nombre: Anth'Zz Berrocal<br>⚡ Alias: BerMatModZ<br>📍 Ubicación: Andahuaylas, Perú<br>📱 Contacto: 937556459<br>🧠 Especialidades: Python, Bots IA, Hacking Ético, Web avanzada<br>💻 Proyectos: BerMat-Bot MD🔥, Simulador Hacker, Web Interactiva",
      ".bermat ayuda": "🤖 Ayuda de comandos:<br>Usa comandos como .BerMat hack, .BerMat sistema, .BerMat novia, .BerMat info para explorar las capacidades del bot IA BerMat.",
      ".bermat verso": "📝 “En cada script que escribo, y cada variable que declaro,<br>mi corazón late fuerte por ti, mi reina Briyidth, mi faro.” 💕"
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
      const response = responses[text.toLowerCase()] || "⚠️ Comando no reconocido. Escribe <code>.BerMat menu</code> para ver opciones.";
      botMsg.innerHTML = response;
      chat.appendChild(botMsg);

      chat.scrollTop = chat.scrollHeight;
      input.value = "";
    }
  </script></body>
</html>
