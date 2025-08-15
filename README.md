
<html lang="es">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>⚡ BerMat — Windows 11 Web</title>
<style>
:root {
  --bg: #0f1724;
  --glass: rgba(255,255,255,0.06);
  --accent: #6ee7b7;
  --task: #0b1220;
  --text: #e6eef8;
  --muted: #9fb0c8;
  font-family: 'Segoe UI', Roboto, system-ui, -apple-system;
}
html, body {
  margin: 0;
  height: 100%;
  background: linear-gradient(180deg, #051025 0%, #081426 50%, #0b1220 100%);
  color: var(--text);
  overflow: hidden;
}
.wallpaper {
  position: fixed;
  inset: 0;
  background: radial-gradient(circle at 30% 30%, rgba(110,231,183,0.12), transparent 30%),
              radial-gradient(circle at 80% 70%, rgba(124,58,237,0.06), transparent 30%);
}
.desktop {
  position: relative;
  height: 100%;
  padding: 20px;
  display: flex;
  flex-wrap: wrap;
  gap: 14px;
}
.icon {
  width: 88px;
  text-align: center;
  cursor: pointer;
}
.icon .img {
  width: 64px;
  height: 64px;
  border-radius: 12px;
  background: var(--glass);
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--accent);
  font-weight: 700;
  box-shadow: 0 4px 12px rgba(0,0,0,0.6);
}
.icon .label {
  font-size: 12px;
  color: var(--muted);
  margin-top: 6px;
}
/* Taskbar */
.taskbar {
  position: fixed;
  left: 0;
  right: 0;
  bottom: 0;
  height: 56px;
  background: rgba(255,255,255,0.05);
  backdrop-filter: blur(8px);
  display: flex;
  align-items: center;
  padding: 0 12px;
}
.start {
  width: 44px;
  height: 44px;
  border-radius: 10px;
  background: var(--glass);
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
}
.tray {
  margin-left: auto;
  display: flex;
  gap: 10px;
  align-items: center;
}
.tray .btn {
  padding: 6px 10px;
  border-radius: 8px;
  background: rgba(255,255,255,0.02);
  color: var(--muted);
}
/* Window */
.window {
  position: absolute;
  background: rgba(255,255,255,0.03);
  border-radius: 12px;
  border: 1px solid rgba(255,255,255,0.08);
  width: 700px;
  max-width: calc(100% - 40px);
  height: 480px;
  display: none;
  flex-direction: column;
  box-shadow: 0 12px 40px rgba(0,0,0,0.7);
}
.titlebar {
  height: 44px;
  display: flex;
  align-items: center;
  padding: 0 10px;
  background: rgba(255,255,255,0.05);
  cursor: move;
}
.titlebar .title {
  font-weight: 600;
}
.controls {
  margin-left: auto;
  display: flex;
  gap: 8px;
}
.ctrl {
  width: 30px;
  height: 26px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
}
.win-body {
  padding: 12px;
  overflow: auto;
  flex: 1;
}
.avatar {
  width: 100px;
  height: 100px;
  border-radius: 16px;
  background: linear-gradient(135deg, var(--accent), #7c3aed);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 28px;
  font-weight: 700;
  color: #021018;
}
.gallery img {
  width: 150px;
  height: 100px;
  object-fit: cover;
  border-radius: 8px;
  cursor: pointer;
}
.viewer {
  position: fixed;
  inset: 0;
  background: rgba(0,0,0,0.9);
  display: none;
  align-items: center;
  justify-content: center;
}
.viewer img {
  max-width: 90%;
  max-height: 90%;
}
</style>
</head>
<body>
<div class="wallpaper"></div>

<div class="desktop">
  <div class="icon" onclick="openWin('about')">
    <div class="img">BM</div>
    <div class="label">Sobre mí</div>
  </div>
  <div class="icon" onclick="openWin('projects')">
    <div class="img">⚡</div>
    <div class="label">Proyectos</div>
  </div>
  <div class="icon" onclick="openWin('gallery')">
    <div class="img">📷</div>
    <div class="label">Galería</div>
  </div>
</div>

<div class="taskbar">
  <div class="start" onclick="alert('Menú inicio en construcción')">☰</div>
  <div class="tray">
    <div class="btn">Andahuaylas</div>
    <div class="btn">ESP</div>
    <div class="btn" id="clock"></div>
  </div>
</div>

<!-- Ventanas -->
<div id="about" class="window" style="left:100px; top:80px;">
  <div class="titlebar"><span class="title">Sobre Anth'Zz Berrocal</span>
    <div class="controls"><div class="ctrl" onclick="closeWin('about')">✕</div></div>
  </div>
  <div class="win-body">
    <div class="avatar">AB</div>
    <h2>Anth'Zz Berrocal</h2>
    <p><b>Alias:</b> BerMatModZ — <b>Proyecto:</b> ⚡BerMat-Bot MD🔥</p>
    <p><b>Ubicación:</b> Andahuaylas</p>
    <p><b>Mensaje:</b> 💖 TE AMO MUCHÍSIMO MI REINA Mi BriyidthCha</p>
    <p><b>GitHub:</b> <a href="https://github.com/AnthZz-Berrocal" target="_blank">Abrir perfil</a></p>
  </div>
</div>

<div id="projects" class="window" style="left:160px; top:140px;">
  <div class="titlebar"><span class="title">Proyectos</span>
    <div class="controls"><div class="ctrl" onclick="closeWin('projects')">✕</div></div>
  </div>
  <div class="win-body">
    <ul>
      <li>⚡ BerMat-Bot MD🔥 — Bot de WhatsApp</li>
      <li>BerMat_Mods — Automatizaciones</li>
      <li>Webs estilo hacker y Windows 11</li>
    </ul>
  </div>
</div>

<div id="gallery" class="window" style="left:200px; top:200px;">
  <div class="titlebar"><span class="title">Galería</span>
    <div class="controls"><div class="ctrl" onclick="closeWin('gallery')">✕</div></div>
  </div>
  <div class="win-body gallery">
    <img src="https://picsum.photos/400/300?1" onclick="viewImg(this.src)">
    <img src="https://picsum.photos/400/300?2" onclick="viewImg(this.src)">
    <img src="https://picsum.photos/400/300?3" onclick="viewImg(this.src)">
  </div>
</div>

<!-- Visor de imágenes -->
<div class="viewer" id="viewer" onclick="this.style.display='none'">
  <img src="" alt="">
</div>

<script>
function openWin(id) {
  document.getElementById(id).style.display = 'flex';
}
function closeWin(id) {
  document.getElementById(id).style.display = 'none';
}
function viewImg(src) {
  document.getElementById('viewer').style.display = 'flex';
  document.querySelector('#viewer img').src = src;
}
setInterval(()=>{
  document.getElementById('clock').textContent = new Date().toLocaleTimeString();
},1000);
</script>
</body>
</html>
