
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Mi Reina  Hermosa Kath 💖</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(135deg, #ffecd2 0%, #fcb69f 100%);
      height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      overflow: hidden;
      color: #333;
      text-align: center;
    }

    .title {
      font-family: 'Dancing Script', cursive;
      font-size: 3.5rem;
      color: #e91e63;
      text-shadow: 0 0 10px rgba(233, 30, 99, 0.3);
      margin-bottom: 1rem;
      animation: float 3s ease-in-out infinite;
    }

    .subtitle {
      font-size: 1.3rem;
      color: #555;
      margin-bottom: 2rem;
      max-width: 80%;
    }

    .button-group {
      display: flex;
      gap: 2rem;
    }

    .btn {
      padding: 1rem 2rem;
      font-size: 1.2rem;
      border: none;
      border-radius: 50px;
      cursor: pointer;
      transition: all 0.3s ease;
      font-weight: 600;
      box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
    }

    .btn.yes {
      background: linear-gradient(45deg, #ff4081, #e91e63);
      color: white;
    }

    .btn.no {
      background: linear-gradient(45deg, #6c757d, #5a6268);
      color: white;
    }

    .btn:hover {
      transform: scale(1.1);
      box-shadow: 0 6px 20px rgba(0, 0, 0, 0.3);
    }

    .btn.small {
      padding: 0.7rem 1.5rem;
      font-size: 1rem;
    }

    @keyframes float {
      0% { transform: translateY(0px); }
      50% { transform: translateY(-10px); }
      100% { transform: translateY(0px); }
    }

    /* Modal */
    .modal {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.6);
      display: flex;
      justify-content: center;
      align-items: center;
      z-index: 100;
      animation: fadeIn 0.5s ease;
    }

    .modal.hidden {
      opacity: 0;
      pointer-events: none;
    }

    .modal-content, .final-content {
      background: white;
      padding: 2rem;
      border-radius: 20px;
      width: 80%;
      max-width: 400px;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
      border: 4px solid #ff4081;
      animation: popUp 0.5s ease;
      text-align: center;
      position: relative;
      overflow: hidden;
    }

    .modal-content::before {
      content: "";
      position: absolute;
      top: -10px;
      left: -10px;
      right: -10px;
      bottom: -10px;
      border: 2px solid transparent;
      border-radius: 25px;
      background: linear-gradient(45deg, #ff4081, #ff6b6b, #ffec40, #40c0ff) border-box;
      -webkit-mask: linear-gradient(#fff 0 0) padding-box, linear-gradient(#fff 0 0);
      -webkit-mask-composite: destination-out;
      mask-composite: exclude;
      pointer-events: none;
      z-index: -1;
    }

    .modal-buttons {
      margin-top: 1.5rem;
      display: flex;
      justify-content: center;
      gap: 1rem;
    }

    .final-content h2 {
      font-family: 'Dancing Script', cursive;
      font-size: 2.5rem;
      color: #e91e63;
      margin-bottom: 1rem;
    }

    .final-text {
      font-size: 1.2rem;
      color: #333;
      margin-bottom: 1.5rem;
      line-height: 1.6;
      animation: glowText 2s ease-in-out infinite alternate;
    }

    .kiss-gif {
      width: 150px;
      height: auto;
      border-radius: 10px;
      box-shadow: 0 0 15px rgba(255, 105, 180, 0.5);
      border: 3px solid #ff69b4;
      animation: pulse 1.5s ease infinite;
    }

    @keyframes fadeIn {
      from { opacity: 0; }
      to { opacity: 1; }
    }

    @keyframes popUp {
      from { opacity: 0; transform: scale(0.7); }
      to { opacity: 1; transform: scale(1); }
    }

    @keyframes glowText {
      from { text-shadow: 0 0 5px #ff4081; }
      to { text-shadow: 0 0 20px #ff4081, 0 0 30px #ff6b64; }
    }

    @keyframes pulse {
      0% { transform: scale(1); }
      50% { transform: scale(1.05); }
      100% { transform: scale(1); }
    }

    /* Corazones flotantes */
    .heart {
      position: fixed;
      font-size: 20px;
      color: #ff4081;
      pointer-events: none;
      user-select: none;
      animation: floatHeart linear infinite;
      opacity: 0;
    }

    @keyframes floatHeart {
      0% {
        transform: translateY(0) rotate(0deg);
        opacity: 0;
      }
      20% {
        opacity: 1;
      }
      100% {
        transform: translateY(-100vh) rotate(360deg);
        opacity: 0;
      }
    }

    /* Footer */
    .footer {
      margin-top: 2rem;
      font-size: 0.9rem;
      color: #666;
      font-family: 'Poppins', sans-serif;
      font-style: italic;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1 class="title">Mi Reina Hermosa Kath 💖</h1>
    <p class="subtitle">¿Puedes pasarme fotos de ti para conocerte más? 😍</p>

    <div class="button-group">
      <button id="yesBtn" class="btn yes">Sí</button>
      <button id="noBtn" class="btn no">No</button>
    </div>
  </div>

  <!-- Modal de confirmación -->
  <div id="confirmModal" class="modal hidden">
    <div class="modal-content">
      <p>¿Estás segura que no me quieres pasar tus fotos? 😢</p>
      <div class="modal-buttons">
        <button id="confirmYes" class="btn yes small">Sí</button>
        <button id="confirmNo" class="btn no small">No</button>
      </div>
    </div>
  </div>

  <!-- Modal final -->
  <div id="finalModal" class="modal hidden">
    <div class="final-content">
      <h2>¡Sabía que dirías que sí! 🎉</h2>
      <p class="final-text">¡Eres la mejor persona del mundo! 💕 Por favor, pásame tus fotos... ¡sí o sí! 😉</p>
      <img src="https://media1.giphy.com/media/v1.Y2lkPTZjMDliOTUyeGg2dGpwZzMxN3Z5Z3BrM2llOGkyY2FsM3ByY3NybnppeXUydGdheSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/eb0AqcVIVCaheKcDH0/giphy.gif" alt="Besito de gatito" class="kiss-gif" />
    </div>
  </div>

  <div class="footer">mi by AnthZz Berrocal creado con amor ❤️</div>

  <script>
    // Corazones flotando
    function createHeart() {
      const heart = document.createElement("div");
      heart.className = "heart";
      heart.innerHTML = "❤️";
      heart.style.left = Math.random() * window.innerWidth + "px";
      heart.style.bottom = "0";
      heart.style.animationDuration = Math.random() * 3 + 2 + "s";
      document.body.appendChild(heart);

      setTimeout(() => {
        heart.remove();
      }, 5000);
    }

    // Botones
    const yesBtn = document.getElementById("yesBtn");
    const noBtn = document.getElementById("noBtn");
    const confirmModal = document.getElementById("confirmModal");
    const finalModal = document.getElementById("finalModal");
    const confirmYes = document.getElementById("confirmYes");
    const confirmNo = document.getElementById("confirmNo");

    // Al hacer clic en "Sí"
    yesBtn.addEventListener("click", () => {
      finalModal.classList.remove("hidden");
      // Crear corazones cada 300ms por 5 segundos
      const heartInterval = setInterval(createHeart, 300);
      setTimeout(() => clearInterval(heartInterval), 5000);
    });

    // Al hacer clic en "No"
    noBtn.addEventListener("click", () => {
      confirmModal.classList.remove("hidden");
    });

    // Confirmación: "Sí, no quiero"
    confirmYes.addEventListener("click", () => {
      alert("¡No vale! 😤 ¡Tienes que decir que sí!");
      confirmModal.classList.add("hidden");
      moveNoButton();
    });

    // Confirmación: "No, sí quiero"
    confirmNo.addEventListener("click", () => {
      confirmModal.classList.add("hidden");
      finalModal.classList.remove("hidden");
      const heartInterval = setInterval(createHeart, 300);
      setTimeout(() => clearInterval(heartInterval), 5000);
    });

    // Mover el botón "No" aleatoriamente
    function moveNoButton() {
      const maxX = window.innerWidth - noBtn.offsetWidth;
      const maxY = window.innerHeight - noBtn.offsetHeight;

      const randomX = Math.max(100, Math.floor(Math.random() * (maxX - 200)));
      const randomY = Math.max(100, Math.floor(Math.random() * (maxY - 200)));

      noBtn.style.position = "fixed";
      noBtn.style.left = `${randomX}px`;
      noBtn.style.top = `${randomY}px`;

      noBtn.style.transform = "scale(1.3)";
      setTimeout(() => {
        noBtn.style.transform = "scale(1)";
      }, 200);
    }

    // Huir al pasar el mouse
    noBtn.addEventListener("mouseenter", () => {
      moveNoButton();
    });
  </script>
</body>
</html>
