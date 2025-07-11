<!DOCTYPE html><html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>🔥 BerMat Battle Royale 🔫</title>
  <style>
    * { box-sizing: border-box; }
    body {
      margin: 0;
      font-family: 'Segoe UI', sans-serif;
      background-color: #0d0d0d;
      color: #ffffff;
      overflow: hidden;
    }
    #gameCanvas {
      background: url('https://i.postimg.cc/B6dRjvrv/battle-bg.jpg') no-repeat center center;
      background-size: cover;
      display: block;
      margin: 0 auto;
      border: 4px solid #00ff99;
    }
    .info-bar {
      text-align: center;
      padding: 10px;
      background: #000;
      border-bottom: 2px solid #00ff99;
      font-size: 14px;
    }
    .controls {
      position: fixed;
      bottom: 20px;
      left: 50%;
      transform: translateX(-50%);
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      justify-content: center;
    }
    .controls button {
      padding: 12px 22px;
      font-weight: bold;
      background: #00ff99;
      color: #000;
      border: none;
      border-radius: 10px;
      cursor: pointer;
      box-shadow: 0 0 10px #00ff99;
    }
    #menuOverlay, #gameOverScreen {
      position: absolute;
      top: 0; left: 0;
      width: 100%; height: 100%;
      background: rgba(0,0,0,0.9);
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      color: #00ff99;
      z-index: 9999;
    }
    #menuOverlay h1, #gameOverScreen h1 {
      font-size: 3rem;
      margin-bottom: 20px;
    }
    #menuOverlay button, #gameOverScreen button {
      font-size: 1.5rem;
      padding: 10px 20px;
      background: #00ff99;
      border: none;
      border-radius: 10px;
      cursor: pointer;
    }
    #scoreDisplay {
      position: absolute;
      top: 10px;
      right: 20px;
      background: rgba(0,0,0,0.6);
      padding: 10px 20px;
      border-radius: 10px;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <div id="menuOverlay">
    <h1>🎮 BerMat Battle Royale</h1>
    <p>🔥 Creador: <strong>AnthZz Berrocal (BerMatModZ)</strong></p>
    <p>💻 Bots, IA, Seguridad, Automatización</p>
    <button onclick="startGame()">Iniciar Partida</button>
  </div>  <div id="gameOverScreen" style="display: none;">
    <h1>💀 GAME OVER</h1>
    <p>Tu puntaje fue: <span id="finalScore">0</span></p>
    <button onclick="restartGame()">Volver a Jugar</button>
  </div>  <div class="info-bar">
    <h2>👾 BerMat Battle Royale v4.0</h2>
    <p><strong>Creado por:</strong> AnthZz Berrocal — <strong>Alias:</strong> BerMatModZ | 📍 Andahuaylas</p>
    <p>⚙️ Bots de WhatsApp • IA • Automatización • Seguridad Digital Ética</p>
  </div><canvas id="gameCanvas" width="1000" height="600"></canvas>

  <div id="scoreDisplay">Puntaje: <span id="score">0</span></div>  <div class="controls">
    <button onclick="move('up')">⬆️</button>
    <button onclick="move('left')">⬅️</button>
    <button onclick="move('right')">➡️</button>
    <button onclick="move('down')">⬇️</button>
    <button onclick="shoot()">🔫</button>
  </div><audio id="bgMusic" src="https://cdn.pixabay.com/download/audio/2022/03/21/audio_b62cbabb5c.mp3?filename=tech-ambient-113626.mp3" loop></audio> <audio id="shootSound" src="https://cdn.pixabay.com/download/audio/2021/09/07/audio_385ed8e298.mp3?filename=laser-gun-81230.mp3"></audio> <audio id="explosionSound" src="https://cdn.pixabay.com/download/audio/2021/10/19/audio_c6326c1c5e.mp3?filename=explosion-6055.mp3"></audio>

  <script>
    const canvas = document.getElementById('gameCanvas');
    const ctx = canvas.getContext('2d');

    const bgMusic = document.getElementById('bgMusic');
    const shootSound = document.getElementById('shootSound');
    const explosionSound = document.getElementById('explosionSound');

    let started = false;
    let gameOver = false;
    let score = 0;

    const player = {
      x: 100,
      y: 100,
      size: 40,
      speed: 5,
      color: '#00ff99',
      health: 100
    };

    const bullets = [];
    const enemies = [];
    const explosions = [];

    function startGame() {
      document.getElementById('menuOverlay').style.display = 'none';
      bgMusic.play();
      started = true;
      gameOver = false;
      score = 0;
      player.health = 100;
      enemies.length = 0;
      bullets.length = 0;
      updateGame();
    }

    function restartGame() {
      document.getElementById('gameOverScreen').style.display = 'none';
      startGame();
    }

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

    function spawnEnemy() {
      const y = Math.random() * (canvas.height - 40);
      enemies.push({ x: canvas.width, y, size: 40, color: 'orange', health: 20 });
    }

    function drawEnemies() {
      enemies.forEach((e, i) => {
        ctx.fillStyle = e.color;
        ctx.fillRect(e.x, e.y, e.size, e.size);
        e.x -= 2;

        if (e.x < player.x + player.size &&
            e.x + e.size > player.x &&
            e.y < player.y + player.size &&
            e.y + e.size > player.y) {
          player.health -= 10;
          enemies.splice(i, 1);
          if (player.health <= 0) {
            endGame();
          }
        }
      });
    }

    function endGame() {
      started = false;
      gameOver = true;
      document.getElementById('finalScore').textContent = score;
      document.getElementById('gameOverScreen').style.display = 'flex';
      bgMusic.pause();
    }

    function detectCollisions() {
      bullets.forEach((b, bi) => {
        enemies.forEach((e, ei) => {
          if (b.x < e.x + e.size && b.x + 10 > e.x &&
              b.y < e.y + e.size && b.y + 4 > e.y) {
            explosions.push({ x: e.x, y: e.y, timer: 20 });
            explosionSound.play();
            enemies.splice(ei, 1);
            bullets.splice(bi, 1);
            score += 10;
            document.getElementById('score').textContent = score;
          }
        });
      });
    }

    function drawExplosions() {
      explosions.forEach((ex, i) => {
        ctx.fillStyle = `rgba(255,165,0,${ex.timer / 20})`;
        ctx.beginPath();
        ctx.arc(ex.x + 20, ex.y + 20, 30, 0, 2 * Math.PI);
        ctx.fill();
        ex.timer--;
        if (ex.timer <= 0) explosions.splice(i, 1);
      });
    }

    function drawHUD() {
      ctx.fillStyle = '#000';
      ctx.fillRect(0, 0, 200, 40);
      ctx.fillStyle = '#fff';
      ctx.font = 'bold 16px Arial';
      ctx.fillText('Vida: ' + player.health, 10, 25);
    }

    function updateGame() {
      if (!started || gameOver) return;
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      drawPlayer();
      drawBullets();
      drawEnemies();
      drawExplosions();
      detectCollisions();
      drawHUD();
      requestAnimationFrame(updateGame);
    }

    function move(dir) {
      if (dir === 'up') player.y -= player.speed;
      if (dir === 'down') player.y += player.speed;
      if (dir === 'left') player.x -= player.speed;
      if (dir === 'right') player.x += player.speed;
    }

    function shoot() {
      bullets.push({ x: player.x + player.size, y: player.y + player.size / 2 });
      shootSound.play();
    }

    setInterval(() => {
      if (started && !gameOver) spawnEnemy();
    }, 2000);
  </script></body>
</html>
