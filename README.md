<!DOCTYPE html><html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>⚡BerMat-Bot MD🔥 - WhatsApp Simulado</title>
  <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      padding: 0;
      font-family: 'Roboto', sans-serif;
      background-color: #e5ddd5;
    }
    .whatsapp-container {
      width: 100%;
      max-width: 500px;
      height: 100vh;
      margin: 0 auto;
      display: flex;
      flex-direction: column;
      background-color: #fff;
      box-shadow: 0 0 10px rgba(0,0,0,0.2);
    }
    .header {
      background-color: #075e54;
      color: white;
      padding: 10px 15px;
      font-weight: bold;
      font-size: 1.2em;
      display: flex;
      align-items: center;
    }
    .chat-box {
      flex: 1;
      padding: 15px;
      background-image: url('https://i.imgur.com/3M3K0Fz.png');
      background-size: cover;
      overflow-y: auto;
      display: flex;
      flex-direction: column;
    }
    .msg {
      max-width: 75%;
      padding: 10px 14px;
      margin: 8px;
      border-radius: 8px;
      font-size: 0.95em;
      line-height: 1.4em;
      box-shadow: 0 1px 3px rgba(0,0,0,0.1);
    }
    .user {
      align-self: flex-end;
      background-color: #dcf8c6;
    }
    .bot {
      align-self: flex-start;
      background-color: #fff;
    }
    .input-box {
      display: flex;
      padding: 10px;
      border-top: 1px solid #ccc;
      background-color: #f0f0f0;
    }
    input {
      flex: 1;
      padding: 10px;
      border: none;
      border-radius: 20px;
      font-size: 1em;
      outline: none;
      background-color: #fff;
      box-shadow: 0 1px 3px rgba(0,0,0,0.1);
    }
  </style>
</head>
<body>
  <div class="whatsapp-container">
    <div class="header">⚡ BerMat-Bot MD🔥</div>
    <div class="chat-box" id="chat">
      <div class="msg bot">👋 Hola, soy tu bot inteligente ⚡<br>Escribe <strong>.menu</strong>, <strong>.info</strong>, <strong>.hack</strong>, <strong>.verso</strong> y más.</div>
    </div>
    <div class="input-box">
      <input type="text" id="userInput" placeholder="Escribe un mensaje..." onkeydown="if(event.key==='Enter'){sendMessage()}" />
    </div>
  </div>  <script>
    const chat = document.getElementById("chat");
    const responses = {
      ".menu": "📜 Comandos disponibles:<br>- .info<br>- .hack<br>- .darkweb<br>- .verso<br>- .xo<br>- .novia<br>- .sistema<br>- .creditos",
      ".info": "👤 Creador: Anth'Zz Berrocal<br>🔗 Alias: BerMatModZ<br>🌍 Ciudad: Andahuaylas<br>📱 WhatsApp: 937556459<br>🛠️ Proyectos: ⚡BerMat-Bot MD🔥, Bots IA, Webs hacker, Terminal Scripts",
      ".hack": "💻 Iniciando simulación de hackeo...<br>📡 Accediendo a servidor...<br>🔐 Acceso root exitoso ✔️<br>Mensaje: 'Tío pásame el bot cause.'",
      ".darkweb": "🌐 Accediendo a nodo secreto...<br>Conexión cifrada. Identificado como BerMatModZ<br>🧠 Nivel de seguridad: MÁXIMO",
      ".verso": "❤️ 'Eres mi reina, Briyidth Jhorgina,<br>En mi código tú eres la rutina más divina'",
      ".xo": "🎮 Partida de XO:<br>[❌ | 🟢 | ⬜]<br>[⬜ | ❌ | ⬜]<br>[⬜ | ⬜ | 🟢]",
      ".novia": "💖 Mi reina Briyidth Jhorgina, eres mi todo. Gracias por estar en mi vida 💘",
      ".sistema": "🧠 Sistema: BerMatOS X-AI<br>Motor IA: BerMat-Core v3.0<br>Seguridad: Nivel militar<br>Estado: ACTIVO 24/7",
      ".creditos": "⚡ Desarrollado por Anth'Zz Berrocal | BerMatModZ<br>Hecho con amor, código y pasión hacker 🇵🇪"
    };

    function sendMessage() {
      const input = document.getElementById("userInput");
      const text = input.value.trim();
      if (!text) return;

      const userMsg = document.createElement("div");
      userMsg.className = "msg user";
      userMsg.textContent = text;
      chat.appendChild(userMsg);

      const botMsg = document.createElement("div");
      botMsg.className = "msg bot";
      const response = responses[text.toLowerCase()] || "⚠️ Comando no reconocido. Escribe <strong>.menu</strong> para ver opciones.";
      botMsg.innerHTML = response;
      chat.appendChild(botMsg);

      chat.scrollTop = chat.scrollHeight;
      input.value = "";
    }
  </script></body>
</html>
