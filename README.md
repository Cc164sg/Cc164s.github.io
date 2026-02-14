<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Feliz San Valentín ❤️</title>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    min-height: 100vh;
    overflow: hidden;
    font-family: 'Segoe UI', Arial, sans-serif;
    text-align: center;
    background: linear-gradient(135deg, #ff9a9e 0%, #fad0c4 100%);
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    position: relative;
    transition: background-color 1s ease;
}

body.rojo {
    background: #ff4d4d !important;
}

/* Fondo sutil */
body::before {
    content: "❤️";
    font-size: 120px;
    position: fixed;
    width: 100%;
    height: 100%;
    opacity: 0.03;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    align-items: center;
    pointer-events: none;
}

h1 {
    font-size: 2.5em;
    color: #d63031;
    z-index: 10;
    margin-bottom: 20px;
    font-weight: 400;
}

.pregunta {
    font-size: 1.8em;
    color: #e84342;
    z-index: 10;
    margin: 20px 0;
    font-weight: 300;
}

.botones {
    margin-top: 30px;
    position: relative;
    width: 100%;
    max-width: 500px;
    height: 120px;
    z-index: 10;
}

button {
    padding: 15px 40px;
    font-size: 1.3em;
    border: none;
    border-radius: 40px;
    cursor: pointer;
    position: absolute;
    transition: all 0.3s ease;
    box-shadow: 0 2px 10px rgba(0,0,0,0.1);
    font-weight: 300;
    letter-spacing: 1px;
}

#si {
    background: #ff7675;
    color: white;
    left: 5%;
    border: 1px solid #fff;
}

#si:hover {
    background: #ff6b6b;
    transform: scale(1.05);
}

#si.creciendo {
    transition: all 0.5s ease;
}

#no {
    background: #b2bec3;
    color: #2d3436;
    right: 5%;
    border: 1px solid #dfe6e9;
}

#no:hover {
    background: #a4b0be;
}

#no.oculto {
    opacity: 0;
    pointer-events: none;
    transition: opacity 0.5s ease;
}

/* Mensaje central minimalista */
.mensaje-central {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%) scale(0);
    font-size: 3.5em;
    color: white;
    text-shadow: 0 2px 10px rgba(0,0,0,0.2);
    z-index: 2000;
    text-align: center;
    animation: aparecerCentral 0.8s ease-out forwards;
    font-weight: 300;
    background: rgba(255, 255, 255, 0.1);
    padding: 20px 40px;
    border-radius: 60px;
    backdrop-filter: blur(5px);
    border: 1px solid rgba(255,255,255,0.3);
    pointer-events: none;
    white-space: nowrap;
}

@keyframes aparecerCentral {
    0% { transform: translate(-50%, -50%) scale(0); opacity: 0; }
    100% { transform: translate(-50%, -50%) scale(1); opacity: 1; }
}

/* Mensajes en bordes - minimalistas */
.mensaje-borde {
    position: fixed;
    font-size: 1.2em;
    color: white;
    padding: 8px 16px;
    background: rgba(255, 120, 120, 0.2);
    border-radius: 30px;
    backdrop-filter: blur(4px);
    border: 1px solid rgba(255,255,255,0.2);
    white-space: nowrap;
    z-index: 1000;
    animation: fadeInOut 3s ease forwards;
    pointer-events: none;
    font-weight: 300;
    letter-spacing: 0.5px;
}

@keyframes fadeInOut {
    0% { opacity: 0; transform: scale(0.8); }
    15% { opacity: 1; transform: scale(1); }
    85% { opacity: 1; transform: scale(1); }
    100% { opacity: 0; transform: scale(0.8); }
}

/* Posiciones fijas para mensajes */
.mensaje-arriba {
    top: 20px;
    left: 50%;
    transform: translateX(-50%);
}

.mensaje-abajo {
    bottom: 20px;
    left: 50%;
    transform: translateX(-50%);
}

.mensaje-izquierda {
    left: 20px;
    top: 50%;
    transform: translateY(-50%);
}

.mensaje-derecha {
    right: 20px;
    top: 50%;
    transform: translateY(-50%);
}

.mensaje-esquina-superior-izquierda {
    top: 20px;
    left: 20px;
}

.mensaje-esquina-superior-derecha {
    top: 20px;
    right: 20px;
}

.mensaje-esquina-inferior-izquierda {
    bottom: 20px;
    left: 20px;
}

.mensaje-esquina-inferior-derecha {
    bottom: 20px;
    right: 20px;
}

/* Contador minimalista */
.contador-intentos {
    position: fixed;
    bottom: 15px;
    left: 15px;
    background: rgba(255,255,255,0.2);
    padding: 6px 12px;
    border-radius: 20px;
    color: #4a4a4a;
    font-size: 0.9em;
    backdrop-filter: blur(4px);
    z-index: 20;
    border: 1px solid rgba(255,255,255,0.3);
}

/* Corazones minimalistas */
.corazon {
    position: fixed;
    color: #ff4d4d;
    font-size: 20px;
    pointer-events: none;
    z-index: 100;
    opacity: 0.7;
    animation: flotar 3s linear forwards;
}

@keyframes flotar {
    0% {
        transform: translateY(0) scale(1);
        opacity: 0.7;
    }
    100% {
        transform: translateY(-100px) scale(1.2);
        opacity: 0;
    }
}

/* Corazones de lluvia minimalistas */
.corazon-lluvia {
    position: fixed;
    color: #ff6b6b;
    font-size: 16px;
    pointer-events: none;
    z-index: 50;
    opacity: 0.5;
    animation: llover 4s linear forwards;
}

@keyframes llover {
    0% {
        transform: translateY(-10vh) rotate(0deg);
        opacity: 0.5;
    }
    100% {
        transform: translateY(110vh) rotate(20deg);
        opacity: 0;
    }
}

/* Indicador de progreso minimalista */
.progreso-container {
    position: fixed;
    top: 15px;
    right: 15px;
    background: rgba(255,255,255,0.2);
    padding: 8px 15px;
    border-radius: 30px;
    color: #4a4a4a;
    font-size: 0.9em;
    backdrop-filter: blur(4px);
    z-index: 20;
    border: 1px solid rgba(255,255,255,0.3);
}

.barra-progreso {
    width: 120px;
    height: 4px;
    background: rgba(0,0,0,0.1);
    border-radius: 2px;
    margin-top: 5px;
    overflow: hidden;
}

.progreso-llenado {
    height: 100%;
    width: 0%;
    background: #ff7675;
    transition: width 0.3s ease;
}
</style>
</head>

<body>

<h1>Feliz San Valentín</h1>

<div class="pregunta">¿Quieres ser mi Valentín?</div>

<div class="botones">
    <button id="si">Sí</button>
    <button id="no">No</button>
</div>

<!-- Contador de intentos -->
<div class="contador-intentos" id="contadorIntentos">
    Intentos: <span id="intentosNo">0/5</span>
</div>

<!-- Indicador de progreso -->
<div class="progreso-container">
    <div>Progreso</div>
    <div class="barra-progreso">
        <div class="progreso-llenado" id="barraProgreso"></div>
    </div>
</div>

<script>
// Elementos del DOM
const botonNo = document.getElementById("no");
const botonSi = document.getElementById("si");
const intentosSpan = document.getElementById("intentosNo");
const barraProgreso = document.getElementById("barraProgreso");
const body = document.body;

// Variables
let intentosNo = 0;
const MAX_INTENTOS = 5;
let crecimientoActivo = false;
let escalaActual = 1;
let yaMostroMensajeCentral = false; // <-- NUEVA VARIABLE PARA CONTROLAR

const mensajesBorde = [
    "Casi", "Un paso más", "Sigue intentando",
    "El amor es paciente", "No te rindas", "Confía",
    "Último intento", "Sí", "Tú puedes"
];

// Función para mostrar el mensaje central "yo también, tiamo"
function mostrarMensajeCentral() {
    // SOLO mostrar si no se ha mostrado antes
    if (yaMostroMensajeCentral) return;
    yaMostroMensajeCentral = true;
    
    // Crear el mensaje central
    const mensajeCentral = document.createElement('div');
    mensajeCentral.className = 'mensaje-central';
    mensajeCentral.textContent = 'yo también, tiamo';
    
    document.body.appendChild(mensajeCentral);
    
    // Poner la página roja
    body.classList.add('rojo');
    
    // Ocultar elementos originales
    document.querySelector('h1').style.opacity = '0';
    document.querySelector('.pregunta').style.opacity = '0';
    document.querySelector('.botones').style.opacity = '0';
    document.querySelector('.contador-intentos').style.opacity = '0';
    document.querySelector('.progreso-container').style.opacity = '0';
    
    // Crear corazones minimalistas
    for (let i = 0; i < 30; i++) {
        setTimeout(() => {
            crearCorazonSimple();
        }, i * 50);
    }
    
    // Lluvia suave de corazones
    for (let i = 0; i < 20; i++) {
        setTimeout(() => {
            crearLluviaSimple();
        }, i * 100);
    }
}

// Corazón simple
function crearCorazonSimple() {
    const corazon = document.createElement('div');
    corazon.className = 'corazon';
    corazon.textContent = '❤️';
    corazon.style.left = Math.random() * 100 + '%';
    corazon.style.top = Math.random() * 100 + '%';
    corazon.style.fontSize = (15 + Math.random() * 20) + 'px';
    corazon.style.animationDuration = (2 + Math.random() * 2) + 's';
    document.body.appendChild(corazon);
    setTimeout(() => corazon.remove(), 3000);
}

// Lluvia simple
function crearLluviaSimple() {
    const corazon = document.createElement('div');
    corazon.className = 'corazon-lluvia';
    corazon.textContent = '❤️';
    corazon.style.left = Math.random() * 100 + '%';
    corazon.style.fontSize = (12 + Math.random() * 15) + 'px';
    corazon.style.animationDuration = (3 + Math.random() * 2) + 's';
    document.body.appendChild(corazon);
    setTimeout(() => corazon.remove(), 5000);
}

// Evento click en botón SÍ
botonSi.addEventListener("click", () => {
    mostrarMensajeCentral();
});

// Actualizar progreso
function actualizarProgreso() {
    const progreso = (intentosNo / MAX_INTENTOS) * 100;
    barraProgreso.style.width = progreso + '%';
    intentosSpan.textContent = intentosNo + '/' + MAX_INTENTOS;
}

// Crear mensaje en borde
function crearMensajeEnBorde() {
    const posiciones = [
        'arriba', 'abajo', 'izquierda', 'derecha',
        'esquina-superior-izquierda', 'esquina-superior-derecha',
        'esquina-inferior-izquierda', 'esquina-inferior-derecha'
    ];
    
    const posicion = posiciones[Math.floor(Math.random() * posiciones.length)];
    
    const mensaje = document.createElement('div');
    mensaje.className = `mensaje-borde mensaje-${posicion}`;
    
    if (intentosNo === MAX_INTENTOS - 1) {
        mensaje.textContent = "Último intento ❤️";
    } else {
        mensaje.textContent = mensajesBorde[Math.floor(Math.random() * mensajesBorde.length)] + ' ❤️';
    }
    
    document.body.appendChild(mensaje);
    
    setTimeout(() => {
        mensaje.remove();
    }, 2900);
}

// Agrandar botón Sí
function agrandarBotonSi() {
    if (!crecimientoActivo) {
        crecimientoActivo = true;
    }
    
    escalaActual = 1 + (intentosNo * 0.5);
    botonSi.style.transform = `scale(${escalaActual})`;
    botonSi.style.zIndex = 100;
    
    const rect = botonSi.getBoundingClientRect();
    const windowWidth = window.innerWidth;
    const windowHeight = window.innerHeight;
    
    const leftPos = (windowWidth / 2) - (rect.width * escalaActual / 2);
    const topPos = (windowHeight / 2) - (rect.height * escalaActual / 2);
    
    botonSi.style.left = leftPos + 'px';
    botonSi.style.top = topPos + 'px';
    botonSi.style.position = 'fixed';
    
    // Crear mensaje
    crearMensajeEnBorde();
    
    // Crear algunos corazones
    for (let i = 0; i < 5; i++) {
        setTimeout(() => {
            crearCorazonSimple();
        }, i * 50);
    }
    
    if (intentosNo >= MAX_INTENTOS) {
        taparBotonNo();
    }
}

// Tapar botón No
function taparBotonNo() {
    botonNo.classList.add('oculto');
    botonSi.style.transform = 'translate(-50%, -50%) scale(8)';
    botonSi.style.left = '50%';
    botonSi.style.top = '50%';
    
    setTimeout(() => {
        mostrarMensajeCentral();
    }, 500);
}

// Click en botón No
botonNo.addEventListener("click", (e) => {
    e.preventDefault();
    e.stopPropagation();
    
    if (intentosNo < MAX_INTENTOS) {
        intentosNo++;
        actualizarProgreso();
        agrandarBotonSi();
        
        // Corazones en el click
        for (let i = 0; i < 3; i++) {
            setTimeout(() => {
                const corazon = document.createElement('div');
                corazon.className = 'corazon';
                corazon.textContent = '❤️';
                corazon.style.left = e.clientX + (Math.random() - 0.5) * 60 + 'px';
                corazon.style.top = e.clientY + (Math.random() - 0.5) * 60 + 'px';
                corazon.style.fontSize = '15px';
                document.body.appendChild(corazon);
                setTimeout(() => corazon.remove(), 2000);
            }, i * 30);
        }
    }
    
    return false;
});

// Posicionar botones
function posicionarBotones() {
    botonSi.style.left = '10%';
    botonSi.style.top = '50%';
    botonSi.style.transform = 'translateY(-50%) scale(1)';
    botonSi.style.position = 'absolute';
    
    botonNo.style.right = '10%';
    botonNo.style.top = '50%';
    botonNo.style.transform = 'translateY(-50%)';
}

// Inicializar
window.addEventListener('load', () => {
    posicionarBotones();
    actualizarProgreso();
});

// Resize
window.addEventListener('resize', () => {
    if (!crecimientoActivo) {
        posicionarBotones();
    }
});
</script>

</body>
</html>
