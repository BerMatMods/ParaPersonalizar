<!DOCTYPE html><html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>🎮 BerMat Battle Royale</title>
  <style>
    * { box-sizing: border-box; }
    body {
      margin: 0;
      background: #000;
      color: #fff;
      font-family: 'Segoe UI', sans-serif;
      overflow: hidden;
    }
    canvas {
      background: url('https://i.postimg.cc/B6dRjvrv/battle-bg.jpg') no-repeat center center;
      background-size: cover;
      display: block;
      margin: 0 auto;
    }
    .hud {
      position: absolute;
      top: 10px;
      left: 10px;
      background: rgba(0,0,0,0.6);
      padding: 10px;
      border-radius: 10px;
      font-weight: bold;
    }
    .branding {
      position: absolute;
      bottom: 10px;
      left: 10px;
      font-size: 12px;
      background: rgba(0,0,0,0.5);
      padding: 5px 10px;
      border-radius: 10px;
    }
    .joystick-container {
      position: fixed;
      bottom: 20px;
      left: 20px;
      width: 120px;
      height: 120px;
    }
    .joystick-base, .joystick-stick {
      position: absolute;
      border-radius: 50%;
      background: rgba(255,255,255,0.1);
    }
    .joystick-base {
      width: 100px;
      height: 100px;
      background: rgba(255,255,255,0.2);
    }
    .joystick-stick {
      width: 60px;
      height: 60px;
      background: rgba(0,255,100,0.7);
      left: 20px;
      top: 20px;
    }
    .fire-button {
      position: fixed;
      bottom: 40px;
      right: 30px;
      width: 80px;
      height: 80px;
      border-radius: 50%;
      background: red;
      color: white;
      font-weight: bold;
      font-size: 16px;
      text-align: center;
      line-height: 80px;
      box-shadow: 0 0 20px red;
    }
  </style>
</head>
<body>
  <canvas id="game" width="1024" height="576"></canvas>
  <div class="hud">
    ❤️ Vida: <span id="life">100</span><br>
    🏆 Score: <span id="score">0</span>
  </div>
  <div class="branding">
    🔥 Creador: <strong>AnthZz Berrocal (BerMatModZ)</strong><br>
    🤖 Bots & IA – Andahuaylas, Perú
  </div>
  <div class="joystick-container">
    <div class="joystick-base"></div>
    <div class="joystick-stick" id="stick"></div>
  </div>
  <div class="fire-button" onclick="shoot()">🔫</div>  <script>
    const canvas = document.getElementById('game');
    const ctx = canvas.getContext('2d');

    let player = { x: 100, y: 100, size: 40, color: '#00ff99', life: 100 };
    let bullets = [];
    let score = 0;

    function drawPlayer() {
      ctx.fillStyle = player.color;
      ctx.fillRect(player.x, player.y, player.size, player.size);
    }

    function drawBullets() {
      bullets.forEach((b, i) => {
        b.x += 7;
        ctx.fillStyle = 'red';
        ctx.fillRect(b.x, b.y, 10, 4);
        if (b.x > canvas.width) bullets.splice(i, 1);
      });
    }

    function shoot() {
      bullets.push({ x: player.x + player.size, y: player.y + player.size / 2 });
    }

    function updateGame() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      drawPlayer();
      drawBullets();
      requestAnimationFrame(updateGame);
    }
    updateGame();

    // JOYSTICK CONTROL
    const stick = document.getElementById('stick');
    let dragging = false, offsetX = 0, offsetY = 0;
    let moveX = 0, moveY = 0;

    stick.addEventListener('touchstart', (e) => {
      dragging = true;
      const touch = e.touches[0];
      offsetX = touch.clientX - stick.offsetLeft;
      offsetY = touch.clientY - stick.offsetTop;
    });

    stick.addEventListener('touchmove', (e) => {
      if (!dragging) return;
      e.preventDefault();
      const touch = e.touches[0];
      let x = touch.clientX - offsetX;
      let y = touch.clientY - offsetY;

      x = Math.max(0, Math.min(60, x));
      y = Math.max(0, Math.min(60, y));

      stick.style.left = x + 'px';
      stick.style.top = y + 'px';

      moveX = (x - 20) / 10;
      moveY = (y - 20) / 10;
    });

    stick.addEventListener('touchend', () => {
      dragging = false;
      stick.style.left = '20px';
      stick.style.top = '20px';
      moveX = 0;
      moveY = 0;
    });

    setInterval(() => {
      player.x += moveX;
      player.y += moveY;
    }, 50);
  </script></body>
</html>
