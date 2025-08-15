
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>HTTP Injector BerMatModZ 🔥</title>
<style>
body {
    margin: 0;
    font-family: 'Consolas', 'Courier New', monospace;
    background: #000;
    color: #0f0;
    display: flex;
    flex-direction: column;
    align-items: center;
    min-height: 100vh;
}
h1 { color: #ff6600; text-align: center; margin-top: 10px; }
h2 { color: #00ff99; text-align: center; margin-bottom: 10px; }
.container { width: 95%; max-width: 1000px; }
.panel {
    background: #111;
    border: 2px solid #00ff00;
    border-radius: 12px;
    padding: 15px;
    margin-bottom: 15px;
}
.btn {
    background: #ff6600;
    color: #000;
    padding: 10px 18px;
    border: none;
    border-radius: 6px;
    cursor: pointer;
    font-weight: bold;
    margin: 3px;
    transition: 0.3s;
}
.btn:hover { background: #ff8533; }
#log {
    background: #000;
    color: #0f0;
    padding: 10px;
    height: 250px;
    overflow-y: auto;
    border-radius: 10px;
    border: 1px solid #0f0;
    font-size: 0.9rem;
}
.info {
    padding: 10px;
    margin-bottom: 10px;
    border: 2px dashed #ff6600;
    border-radius: 8px;
    background: #111a11aa;
}
.info b { color: #ff6600; }
.info span { color: #00ff99; }
.meter { width: 100%; height: 20px; background: #222; border-radius: 10px; overflow: hidden; margin-top: 10px; }
.meter-fill { height: 100%; width: 0%; background: #ff6600; transition: width 0.5s; }
.socials { display: flex; justify-content: center; gap: 15px; margin-top: 10px; }
.socials a { display: inline-block; width: 40px; height: 40px; background: #ff6600; color: #000; border-radius: 50%; display: flex; justify-content: center; align-items: center; text-decoration: none; font-weight: bold; transition: 0.3s; }
.socials a:hover { background: #ff8533; transform: scale(1.2); }
.tabs { display: flex; flex-wrap: wrap; margin-bottom: 10px; }
.tab { padding: 8px 15px; background: #222; margin-right: 5px; cursor: pointer; border-radius: 6px; transition: 0.2s; }
.tab:hover { background: #00ff00; color: #000; }
.tab.active { background: #ff6600; color: #000; }
.tab-content { display: none; background: #111; border: 1px solid #0f0; border-radius: 10px; padding: 10px; }
.tab-content.active { display: block; }
input[type=text], input[type=file] { width: 90%; padding: 8px; margin: 5px 0; border-radius:5px; border:1px solid #0f0; background:#000; color:#0f0; }
</style>
</head>
<body>

<h1>HTTP Injector BerMatModZ 🔥</h1>
<h2>Simulación completa de conexión</h2>

<div class="container">

<div class="panel info">
<b>Nombre:</b> <span>Anth’Zz Berrocal</span><br>
<b>Alias:</b> <span>BerMatModZ</span><br>
<b>Ubicación:</b> <span>Andahuaylas</span><br>
<b>Proyectos:</b> <span>⚡BerMat-Bot MD🔥, BerMat_Mods, BerMatMods_Bot</span><br>
<b>Contacto:</b> <span><a href="https://wa.me/937556459" style="color:#00ff99;">WhatsApp</a></span>
</div>

<div class="panel">
<div class="tabs">
    <div class="tab active" onclick="openTab('connection')">Conexión</div>
    <div class="tab" onclick="openTab('tools')">Herramientas</div>
    <div class="tab" onclick="openTab('import')">Importar/Exportar</div>
    <div class="tab" onclick="openTab('help')">Ayuda</div>
    <div class="tab" onclick="openTab('settings')">Ajustes</div>
</div>

<div id="connection" class="tab-content active">
    <button class="btn" onclick="connect()">Conectar</button>
    <button class="btn" onclick="disconnect()">Desconectar</button>
    <button class="btn" onclick="payload()">Payload</button>
    <button class="btn" onclick="config()">Config</button>
    <div id="status" style="margin-top:10px;">Estado: <b>Desconectado</b></div>
    <div class="meter"><div class="meter-fill" id="meter"></div></div>
    <div style="margin-top:5px;">Velocidad: <b id="speed">0 KB/s</b> | Datos: <b id="data">0 MB</b></div>
    <h3>Registro de conexión:</h3>
    <div id="log"></div>
</div>

<div id="tools" class="tab-content">
<h3>Herramientas simuladas:</h3>
<ul>
<li>Ping a servidor: <button class="btn" onclick="pingServer()">Ping</button></li>
<li>Ver IP y puerto: <button class="btn" onclick="showIP()">Mostrar IP</button></li>
<li>Test de velocidad: <button class="btn" onclick="speedTest()">Test</button></li>
<li>Estadísticas avanzadas: <button class="btn" onclick="stats()">Mostrar</button></li>
</ul>
</div>

<div id="import" class="tab-content">
<h3>Importar / Exportar configuración</h3>
<input type="file" id="importFile"><button class="btn" onclick="importConfig()">Importar</button>
<br>
<input type="text" id="exportName" placeholder="Nombre del archivo"><button class="btn" onclick="exportConfig()">Exportar</button>
</div>

<div id="help" class="tab-content">
<h3>Ayuda / FAQ</h3>
<ul>
<li>Cómo conectar: Presiona "Conectar".</li>
<li>Payload: Ingresa tu payload válido.</li>
<li>Importar/exportar: Selecciona archivo o nombre.</li>
<li>Contactar soporte: <a href="https://wa.me/937556459" style="color:#0f0;">WhatsApp</a></li>
</ul>
</div>

<div id="settings" class="tab-content">
<h3>Ajustes de simulación</h3>
<label>Protocolos:</label>
<select id="protocol">
<option>HTTP</option>
<option>SSH</option>
<option>SSL</option>
<option>TCP</option>
</select><br>
<label>Puerto:</label>
<input type="text" id="port" placeholder="8080"><br>
<label>Proxy:</label>
<input type="text" id="proxy" placeholder="proxy.example.com"><br>
<button class="btn" onclick="saveSettings()">Guardar</button>
</div>

</div>

<div class="socials">
<a href="https://www.facebook.com/anthzz.berrocal" target="_blank">F</a>
<a href="https://www.instagram.com/anthzz.berrocal" target="_blank">I</a>
<a href="https://twitter.com/AnthZz" target="_blank">T</a>
<a href="https://github.com/anthzz" target="_blank">G</a>
</div>

</div>

<script>
let connected=false;
let dataUsed=0;
const userInfo={
    name:"Anth’Zz Berrocal",
    alias:"BerMatModZ",
    location:"Andahuaylas",
    projects:["⚡BerMat-Bot MD🔥","BerMat_Mods","BerMatMods_Bot"]
};

function addLog(msg){
    const time = new Date().toLocaleTimeString();
    document.getElementById('log').innerHTML += `[${time}] ${msg}<br>`;
    document.getElementById('log').scrollTop = document.getElementById('log').scrollHeight;
}

function simulateConnection(){
    addLog("Iniciando secuencia de conexión...");
    document.getElementById('meter').style.width="0%";
    dataUsed=0;
    let progress=0;
    let speed=0;
    const interval = setInterval(()=>{
        progress+=5;
        if(progress>100) progress=100;
        document.getElementById('meter').style.width=progress+"%";
        speed=Math.floor(Math.random()*50+50);
        dataUsed+=speed*0.005;
        document.getElementById('speed').textContent=speed+" KB/s";
        document.getElementById('data').textContent=dataUsed.toFixed(2)+" MB";
        addLog(`Conectando... ${progress}% - Velocidad: ${speed} KB/s - Datos: ${dataUsed.toFixed(2)} MB`);
        if(progress>=100){
            clearInterval(interval);
            connected=true;
            document.getElementById('status').innerHTML='Estado: <b>Conectado ✅</b>';
            addLog(`Conexión establecida!`);
            addLog(`Usuario: ${userInfo.alias} (${userInfo.name})`);
            addLog(`Ubicación: ${userInfo.location}`);
            addLog(`Proyectos activos: ${userInfo.projects.join(", ")}`);
        }
    },500);
}

function connect(){ if(connected) addLog("Ya estás conectado."); else simulateConnection(); }
function disconnect(){ 
    if(!connected) addLog("Ya estás desconectado."); 
    else{
        addLog("Cerrando conexión...");
        setTimeout(()=>{
            connected=false;
            document.getElementById('meter').style.width="0%";
            document.getElementById('speed').textContent="0 KB/s";
            document.getElementById('data').textContent="0 MB";
            document.getElementById('status').innerHTML='Estado: <b>Desconectado</b>';
            addLog("Conexión terminada.");
        },1500);
    } 
}
function payload(){ const p=prompt("Ingresa payload:"); if(p) addLog(`Payload configurado: ${p}`); }
function config(){ addLog("Configuración abierta (simulada)."); }

function openTab(tab){
    document.querySelectorAll('.tab-content').forEach(tc=>tc.classList.remove('active'));
    document.querySelectorAll('.tab').forEach(t=>t.classList.remove('active'));
    document.getElementById(tab).classList.add('active');
    event.currentTarget.classList.add('active');
}

function pingServer(){ addLog("Ping a servidor: 45ms"); }
function showIP(){ addLog("IP simulada: 192.168.1."+Math.floor(Math.random()*255)); }
function speedTest(){ addLog("Velocidad de prueba: "+(Math.floor(Math.random()*80+50))+" KB/s"); }
function stats(){ addLog("Estadísticas: Conexión estable, datos estables, sin errores."); }

function importConfig(){ addLog("Archivo importado (simulado)"); }
function exportConfig(){ const name=document.getElementById('exportName').value||"config"; addLog("Archivo exportado como "+name+".hxi (simulado)"); }
function saveSettings(){ addLog("Ajustes guardados: Puerto "+document.getElementById('port').value+", Proxy "+document.getElementById('proxy').value+", Protocolo "+document.getElementById('protocol').value); }
