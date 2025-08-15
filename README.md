<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>La Magia del Barbero | Barber Shop</title>
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;500;700&display=swap" rel="stylesheet">
<style>
/* ===== RESET ===== */
*{margin:0;padding:0;box-sizing:border-box}
body{font-family:'Poppins',sans-serif;background:#111;color:#fff;line-height:1.6}

/* ===== HEADER ===== */
header{background:#000;padding:20px;text-align:center;border-bottom:3px solid gold}
header h1{font-size:2.5rem;color:gold;text-shadow:0 0 5px rgba(255,215,0,0.6)}
header p{color:#ccc}
nav{display:flex;justify-content:center;gap:20px;margin-top:10px;flex-wrap:wrap}
nav a{color:gold;text-decoration:none;font-weight:500;transition:color .3s}
nav a:hover{color:#fff}

/* ===== SECTION ===== */
section{padding:50px 20px;max-width:1100px;margin:auto}
h2{text-align:center;margin-bottom:20px;font-size:2rem}

/* ===== HERO ===== */
.hero{text-align:center}
.hero svg{width:200px;height:200px;margin-top:20px;filter:drop-shadow(0 0 8px gold)}

/* ===== SERVICES ===== */
.services{display:grid;grid-template-columns:repeat(auto-fit,minmax(250px,1fr));gap:20px}
.service{background:#222;padding:20px;border-radius:10px;text-align:center;box-shadow:0 0 10px rgba(0,0,0,0.5);transition:transform .3s}
.service:hover{transform:translateY(-5px)}
.service svg{width:100%;height:150px;margin-bottom:10px}
.service strong{color:gold;font-size:1.1rem}

/* ===== GALLERY ===== */
.gallery{display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:10px}
.gallery svg{width:100%;height:200px;transition:transform .3s}
.gallery svg:hover{transform:scale(1.05)}

/* ===== CONTACT & BUTTONS ===== */
.contact{text-align:center}
.contact a{display:inline-block;margin:10px;padding:10px 20px;background:gold;color:black;border-radius:5px;text-decoration:none;font-weight:bold;transition:background .3s}
.contact a:hover{background:#d4af37}
button{background:gold;color:black;border:none;padding:10px 20px;margin-top:10px;border-radius:5px;font-weight:bold;cursor:pointer;transition:background .3s}
button:hover{background:#d4af37}

/* ===== DIFERENCIAL ===== */
.diferencial{display:grid;grid-template-columns:repeat(auto-fit,minmax(250px,1fr));gap:20px;text-align:center}
.card{background:#222;padding:20px;border-radius:10px;box-shadow:0 0 10px rgba(0,0,0,0.5)}

/* ===== FOOTER ===== */
footer{background:#000;text-align:center;padding:20px;font-size:.9rem;color:#888;border-top:3px solid gold}
footer strong{color:gold}
</style>
</head>
<body>

<header>
    <h1>La Magia del Barbero</h1>
    <p>Barber Shop – Jirón Alfonso Ugarte, 3er piso</p>
    <p>Horario: Lunes a Domingo – 8:00 AM a 8:00 PM</p>
    <nav>
        <a href="#servicios">Servicios</a>
        <a href="#galeria">Galería</a>
        <a href="#fidelidad">Fidelidad</a>
        <a href="#contacto">Contacto</a>
    </nav>
</header>

<section class="hero">
    <h2>¡Cortes modernos y clásicos con estilo único!</h2>
    <p>Programa de fidelidad: corta tu cabello 4 veces y el 5° es GRATIS.</p>
    <svg viewBox="0 0 64 64" fill="gold">
        <circle cx="32" cy="32" r="30" stroke="gold" stroke-width="4" fill="none"/>
        <path d="M20 40 L44 40 L32 20 Z" fill="gold"/>
    </svg>
</section>

<section id="servicios">
    <h2 style="color: gold;">Nuestros Servicios</h2>
    <div class="services">
        <div class="service">
            <svg viewBox="0 0 64 64" fill="gold"><rect x="10" y="20" width="44" height="24" rx="5"/></svg>
            <h3>Corte Moderno</h3>
            <p>Estilos actuales y personalizados.</p>
            <strong>S/ 25.00</strong>
        </div>
        <div class="service">
            <svg viewBox="0 0 64 64" fill="gold"><circle cx="32" cy="32" r="20"/></svg>
            <h3>Corte Clásico</h3>
            <p>Elegancia atemporal y precisa.</p>
            <strong>S/ 20.00</strong>
        </div>
        <div class="service">
            <svg viewBox="0 0 64 64" fill="gold"><path d="M8 56 L56 8 L56 56 Z"/></svg>
            <h3>Degradado</h3>
            <p>Transiciones suaves y limpias.</p>
            <strong>S/ 28.00</strong>
        </div>
        <div class="service">
            <svg viewBox="0 0 64 64" fill="gold"><path d="M8 32 Q32 56 56 32 Q32 8 8 32 Z"/></svg>
            <h3>Diseño de Barba</h3>
            <p>Perfilado y cuidado profesional.</p>
            <strong>S/ 15.00</strong>
        </div>
    </div>
</section>

<section id="galeria">
    <h2 style="color: gold;">Galería</h2>
    <div class="gallery">
        <svg viewBox="0 0 64 64" fill="gold"><rect x="8" y="8" width="48" height="48"/></svg>
        <svg viewBox="0 0 64 64" fill="gold"><circle cx="32" cy="32" r="24"/></svg>
        <svg viewBox="0 0 64 64" fill="gold"><path d="M8 56 L56 8 L56 56 Z"/></svg>
        <svg viewBox="0 0 64 64" fill="gold"><path d="M8 8 H56 V56 H8 Z"/></svg>
    </div>
</section>

<section id="fidelidad" class="contact">
    <h2 style="color: gold;">Programa de Fidelidad</h2>
    <p>Corta tu cabello 4 veces y el 5° es GRATIS.</p>
    <p id="contador"></p>
    <button onclick="sumarCorte()">Registrar Corte</button>
    <button onclick="reiniciarFidelidad()">Reiniciar</button>
</section>

<section class="diferencial">
    <div class="card">
        <h3>Profesionales Expertos</h3>
        <p>Más de 10 años creando estilos únicos para cada cliente.</p>
    </div>
    <div class="card">
        <h3>Atención Personalizada</h3>
        <p>Escuchamos lo que quieres y lo hacemos realidad.</p>
    </div>
    <div class="card">
        <h3>Ambiente Cómodo</h3>
        <p>Relájate y disfruta de tu corte en un lugar agradable.</p>
    </div>
</section>

<section id="contacto" class="contact">
    <h2 style="color: gold;">Reserva Rápida</h2>
    <a href="https://wa.me/51977355999" target="_blank">WhatsApp 977 355 999</a>
    <a href="https://wa.me/51931538059" target="_blank">WhatsApp 931 538 059</a>
    <p>📍 Jirón Alfonso Ugarte, 3er piso</p>
    <p>📞 977 355 999 | 931 538 059</p>
</section>

<footer>
    © 2025 La Magia del Barbero – Todos los derechos reservados. <br>
    Diseño por <strong>Anth’Zz Berrocal · BerMatModZ</strong>
</footer>

<script>
let cortes = localStorage.getItem("cortes") ? parseInt(localStorage.getItem("cortes")) : 0;
function mostrarCortes(){
    if(cortes >= 4){
        document.getElementById("contador").innerHTML = "🎉 ¡Felicidades! Tu próximo corte es GRATIS.";
    } else {
        document.getElementById("contador").innerHTML = `Has acumulado ${cortes} cortes de 4.`;
    }
}
function sumarCorte(){
    if(cortes < 4){
        cortes++;
        localStorage.setItem("cortes", cortes);
        mostrarCortes();
    }
}
function reiniciarFidelidad(){
    cortes = 0;
    localStorage.setItem("cortes", cortes);
    mostrarCortes();
}
mostrarCortes();
</script>

</body>
</html>
