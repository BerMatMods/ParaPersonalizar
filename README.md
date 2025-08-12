<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>⚡BerMatModZ🔥</title>
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500&family=Roboto:wght@400;700&display=swap" rel="stylesheet">
<script src="https://kit.fontawesome.com/a076d05399.js" crossorigin="anonymous"></script>
<style>
*{margin:0;padding:0;box-sizing:border-box;font-family:'Roboto',sans-serif;}
body{background:#000;color:#fff;overflow-x:hidden;}
/* Fondo Matrix */
canvas#matrix{position:fixed;top:0;left:0;width:100%;height:100%;z-index:-1;}
/* Menú */
.navbar{position:fixed;top:0;left:0;width:100%;background:rgba(0,0,0,0.8);padding:10px;display:flex;align-items:center;z-index:1000;}
.menu-btn{font-size:25px;cursor:pointer;margin-right:20px;}
.menu{position:fixed;top:0;left:-250px;width:250px;height:100%;background:#111;overflow:auto;transition:0.4s;padding-top:60px;}
.menu a{display:block;padding:15px;color:#fff;text-decoration:none;font-size:18px;}
.menu a:hover{background:#ff0000;}
.show{left:0;}
section{padding:100px 20px;min-height:100vh;}
h1{font-family:'Orbitron',sans-serif;font-size:2.5em;text-align:center;margin-bottom:20px;}
p{text-align:center;font-size:18px;line-height:1.6;}
/* Redes */
.social{display:flex;justify-content:center;gap:20px;margin-top:20px;}
.social a{color:#fff;font-size:30px;transition:0.3s;}
.social a:hover{color:#ff0000;transform:scale(1.2);}
</style>
</head>
<body>

<!-- Fondo Matrix -->
<canvas id="matrix"></canvas>

<!-- Navbar -->
<div class="navbar">
  <span class="menu-btn" onclick="toggleMenu()">&#9776;</span>
  <h2>⚡BerMatModZ🔥</h2>
</div>

<!-- Menú Lateral -->
<div id="sideMenu" class="menu">
  <a href="#inicio">Inicio</a>
  <a href="#proyectos">Proyectos</a>
  <a href="#perfil">Perfil</a>
  <a href="#redes">Redes Sociales</a>
  <a href="#briyidth">Mensaje para Briyidth</a>
</div>

<!-- Secciones -->
<section id="inicio">
  <h1>Bienvenido al Mundo de ⚡BerMatModZ🔥</h1>
  <p>Experto en tecnología, hacking y desarrollo de bots avanzados.  
  Aquí encontrarás mis proyectos, perfil y un rincón especial para mi reina ❤️.</p>
</section>

<section id="proyectos">
  <h1>Mis Proyectos</h1>
  <p>✅ ⚡BerMat-Bot MD🔥 – Bot de WhatsApp con IA avanzada y +200 comandos.  
  ✅ BerMat_Mods – Modificaciones y optimizaciones de apps.  
  ✅ Scripts simuladores Anonymous y ciberseguridad visual.  
  ✅ Webs animadas y decoradas al estilo hacker profesional.</p>
</section>

<section id="perfil">
  <h1>Perfil Profesional</h1>
  <p><strong>Nombre:</strong> Anth'Zz Berrocal<br>
  <strong>Alias:</strong> ⚡BerMatModZ🔥<br>
  <strong>Especialidad:</strong> Programación, Hacking Ético, Bots, Automatización.<br>
  <strong>Ubicación:</strong> Andahuaylas, Perú.</p>
</section>

<section id="redes">
  <h1>Mis Redes Sociales</h1>
  <div class="social">
    <a href="https://github.com/BerMatMods" target="_blank"><i class="fab fa-github"></i></a>
    <a href="https://t.me/Berrocal_mdz" target="_blank"><i class="fab fa-telegram"></i></a>
    <a href="https://facebook.com" target="_blank"><i class="fab fa-facebook"></i></a>
    <a href="https://instagram.com" target="_blank"><i class="fab fa-instagram"></i></a>
  </div>
</section>

<section id="briyidth">
  <h1>Para Mi Reina Briyidth 💖</h1>
  <p>Te amo mucho mi amor, mi reina hermosa ❤️.  
  Te doy gracias por llegar a mi vida, eres lo más valioso que tengo y tengo miedo a perderte.  
  Siempre te voy a amar en las buenas y en las malas, y sé que juntos vamos a salir adelante.  
  Te amo muchísimo mi mami 💕.</p>
</section>

<script>
// Menú lateral
function toggleMenu(){
  document.getElementById("sideMenu").classList.toggle("show");
}

// Fondo Matrix
const canvas=document.getElementById('matrix');
const ctx=canvas.getContext('2d');
canvas.height=window.innerHeight;
canvas.width=window.innerWidth;
const letters='01';
const fontSize=14;
const columns=canvas.width/fontSize;
const drops=Array(Math.floor(columns)).fill(1);

function draw(){
  ctx.fillStyle='rgba(0,0,0,0.05)';
  ctx.fillRect(0,0,canvas.width,canvas.height);
  ctx.fillStyle='#0F0';
  ctx.font=fontSize+'px monospace';
  for(let i=0;i<drops.length;i++){
    const text=letters.charAt(Math.floor(Math.random()*letters.length));
    ctx.fillText(text,i*fontSize,drops[i]*fontSize);
    if(drops[i]*fontSize>canvas.height&&Math.random()>0.975)drops[i]=0;
    drops[i]++;
  }
}
setInterval(draw,33);
</script>

</body>
</html>
