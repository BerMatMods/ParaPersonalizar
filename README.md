<!DOCTYPE html><html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
  <title>⚡BerMat-Bot MD🔥</title>
  <link href="https://fonts.googleapis.com/css2?family=Roboto&display=swap" rel="stylesheet">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    body {
      font-family: 'Roboto', sans-serif;
      background-color: #e5ddd5;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      overflow: hidden;
    }
    .app-container {
      width: 100%;
      max-width: 414px;
      height: 736px;
      background-color: #f0f0f0;
      display: flex;
      flex-direction: column;
      box-shadow: 0 0 10px rgba(0,0,0,0.2);
      border-radius: 10px;
      overflow: hidden;
    }
    .header {
      background-color: #075e54;
      color: white;
      padding: 15px;
      font-weight: bold;
      font-size: 1.2em;
    }
    .chat {
      flex: 1;
      padding: 10px;
      background-image: url('https://i.imgur.com/3M3K0Fz.png');
      background-size: cover;
      overflow-y: auto;
      display: flex;
      flex-direction: column;
    }
    .msg {
      max-width: 70%;
      padding: 10px 14px;
      margin: 5px 10px;
      border-radius: 7.5px;
      font-size: 0.95em;
      line-height: 1.4em;
    }
    .user {
      align-self: flex-end;
      background-color: #dcf8c6;
    }
    .bot {
      align-self: flex-start;
      background-color: white;
    }
    .input-container {
      display: flex;
      padding: 8px;
      background-color: #fff;
      border-top: 1px solid #ccc;
    }
    .input-container input {
      flex: 1;
      padding: 10px;
      border: none;
      border-radius: 20px;
      outline: none;
      background-color: #f0f0f0;
      font-size: 1em;
    }
  </style>
</head>
<body>
  <div class="app-container">
    <div class="header">⚡ BerMat-Bot MD🔥</div>
    <div class="chat" id="chat">
      <div class="msg bot">👋 Hola, soy tu bot estilo WhatsApp ⚡<br>Prueba comandos como <strong>.menu</strong>, <strong>.info</strong>, <strong>.hack</strong>, <strong>.verso</strong>...</div>
    </div>
    <div class="input-container">
      <input type="text" id="userInput" placeholder="Escribe un mensaje..." onkeydown="if(event.key==='Enter'){sendMessage()}" />
    </div>
  </div>  <script>
    const chat = document.getElementById("chat");
    const responses = {
      ".menu": "📜 Comandos disponibles:<br>.info, .hack, .darkweb, .verso, .xo, .novia, .sistema, .creditos",
      ".info": "👤 Creador: Anth'Zz Berrocal<br>Alias: BerMatModZ<br>Ciudad: Andahuaylas<br>WhatsApp: 937556459<br>Proyectos: ⚡BerMat-Bot MD🔥, Bots IA, Web Hacker",
      ".hack": "💻 Simulando hackeo...<br>Conectando a servidor...<br>Acceso root exitoso ✔️<br>'Pásame el bot brother.'",
      ".darkweb": "🌐 Accediendo a la darkweb...<br>Identificado como BerMatModZ<br>Nivel de seguridad: ALTO",
      ".verso": "❤️ 'Eres mi reina Briyidth Jhorgina,<br>mi código favorito en cada rutina divina.'",
      ".xo": "🎮 XO:<br>[❌ | 🟢 | ⬜]<br>[⬜ | ❌ | ⬜]<br>[⬜ | ⬜ | 🟢]",
      ".novia": "💖 Te amo mi Briyidth Jhorgina. Eres mi vida 💘",
      ".sistema": "🧠 Sistema BerMatOS X-AI<br>IA Activa 24/7<br>Seguridad de nivel militar",
      ".creditos": "⚡ Creado por Anth'Zz Berrocal | BerMatModZ<br>🇵🇪 Pasión, código y estilo hacker peruano."
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
      const response = responses[text.toLowerCase()] || "⚠️ Comando no reconocido. Usa <strong>.menu</strong> para ver opciones.";
      botMsg.innerHTML = response;
      chat.appendChild(botMsg);

      chat.scrollTop = chat.scrollHeight;
      input.value = "";
    }
  </script></body>
</html>
