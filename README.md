<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Feliz Primer San Valentín ❤️</title>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    min-height: 100vh;
    overflow: hidden;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    text-align: center;
    background: linear-gradient(135deg, #ff758c 0%, #ff7eb3 100%);
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    position: relative;
    transition: background-color 1s ease;
}

body.rojo {
    background: #ff0000 !important;
    animation: palpitar 0.5s ease-in-out infinite;
}

@keyframes palpitar {
    0% { background-color: #ff0000; }
    50% { background-color: #cc0000; }
    100% { background-color: #ff0000; }
}

/* Fondo ositos */
body::before {
    content: "🐻 💖 🐻 💕 🐻 💘 🐻 💞 🐻 💓 🐻 💗 🐻 💝";
    font-size: 80px;
    position: fixed;
    width: 300%;
    height: 300%;
    opacity: 0.1;
    animation: mover 45s linear infinite;
    white-space: nowrap;
    transition: opacity 0.5s ease;
}

body.rojo::before {
    opacity: 0.3;
    content: "❤️ 💖 💘 💝 💕 💞 💓 💗 ❤️ 💖 💘 💝";
}

@keyframes mover {
    0% { transform: translate(0, 0) rotate(0deg); }
    100% { transform: translate(-800px, -400px) rotate(5deg); }
}

h1 {
    font-size: 3.5em;
    color: #fff;
    text-shadow: 2px 2px 4px rgba(255, 0, 110, 0.5);
    z-index: 10;
    animation: latido 1.5s ease-in-out infinite;
    margin-bottom: 20px;
    transition: opacity 0.5s ease;
}

@keyframes latido {
    0% { transform: scale(1); }
    50% { transform: scale(1.05); }
    100% { transform: scale(1); }
}

.pregunta {
    font-size: 2.2em;
    color: #fff;
    text-shadow: 1px 1px 3px rgba(0,0,0,0.2);
    z-index: 10;
    margin: 20px 0;
    transition: opacity 0.5s ease;
}

.botones {
    margin-top: 40px;
    position: relative;
    width: 100%;
    max-width: 600px;
    height: 200px;
    z-index: 10;
    transition: opacity 0.5s ease;
}

button {
    padding: 18px 45px;
    font-size: 1.4em;
    font-weight: bold;
    border: none;
    border-radius: 50px;
    cursor: pointer;
    position: absolute;
    transition: all 0.3s ease;
    box-shadow: 0 4px 15px rgba(0,0,0,0.2);
    white-space: nowrap;
}

#si {
    background: linear-gradient(45deg, #ff4d6d, #ff1e4d);
    color: white;
    left: 10%;
    z-index: 20;
    transition: all 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
}

#si:hover {
    transform: scale(1.1);
    box-shadow: 0 0 30px #ff4d6d;
}

#si.creciendo {
    transition: all 0.8s cubic-bezier(0.68, -0.55, 0.265, 1.55);
}

#no {
    background: linear-gradient(45deg, #6b6b6b, #4a4a4a);
    color: white;
    right: 10%;
    cursor: pointer;
    opacity: 0.9;
    z-index: 30;
    transition: all 0.3s ease;
}

#no:hover {
    background: linear-gradient(45deg, #7a7a7a, #5a5a5a);
}

#no.oculto {
    opacity: 0;
    pointer-events: none;
    transition: opacity 0.5s ease;
}

/* Mensaje central "yo también, tiamo" */
.mensaje-central {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%) scale(0);
    font-size: 5em;
    color: white;
    text-shadow: 5px 5px 10px #990000, 0 0 20px #ffcccc;
    z-index: 2000;
    text-align: center;
    animation: aparecerCentral 1s ease-out forwards;
    white-space: nowrap;
    font-weight: bold;
    background: rgba(255, 50, 50, 0.3);
    padding: 30px 60px;
    border-radius: 100px;
    backdrop-filter: blur(5px);
    border: 4px solid white;
    box-shadow: 0 0 50px rgba(255,255,255,0.5);
    pointer-events: none;
}

.mensaje-central span {
    display: inline-block;
    animation: flotar 2s ease-in-out infinite;
}

@keyframes aparecerCentral {
    0% {
        transform: translate(-50%, -50%) scale(0);
        opacity: 0;
    }
    50% {
        transform: translate(-50%, -50%) scale(1.2);
        opacity: 1;
    }
    100% {
        transform: translate(-50%, -50%) scale(1);
        opacity: 1;
    }
}

@keyframes flotar {
    0%, 100% {
        transform: translateY(0);
    }
    50% {
        transform: translateY(-20px);
    }
}

/* Mensajes en los bordes - AHORA EVITAN EL CENTRO */
.mensaje-borde {
    position: fixed;
    font-size: 1.8em;
    color: white;
    text-shadow: 2px 2px 4px #ff006e;
    font-weight: bold;
    padding: 15px 25px;
    background: rgba(255, 75, 125, 0.7);
    border-radius: 50px;
    backdrop-filter: blur(5px);
    border: 2px solid white;
    white-space: nowrap;
    z-index: 1000;
    animation: aparecerMensaje 0.5s ease-out;
    pointer-events: none;
    max-width: 80vw;
    overflow: hidden;
    text-overflow: ellipsis;
}

@keyframes aparecerMensaje {
    from {
        opacity: 0;
        transform: scale(0.5);
    }
    to {
        opacity: 1;
        transform: scale(1);
    }
}

/* Posiciones para los mensajes - AHORA MÁS CERCA DE LOS BORDES */
.mensaje-arriba {
    top: 20px;
    left: 50%;
    transform: translateX(-50%);
    max-width: 90vw;
}

.mensaje-abajo {
    bottom: 20px;
    left: 50%;
    transform: translateX(-50%);
    max-width: 90vw;
}

.mensaje-izquierda {
    left: 20px;
    top: 50%;
    transform: translateY(-50%);
    max-width: 30vw;
}

.mensaje-derecha {
    right: 20px;
    top: 50%;
    transform: translateY(-50%);
    max-width: 30vw;
}

/* Mensajes en las esquinas - NUEVAS POSICIONES */
.mensaje-esquina-superior-izquierda {
    top: 20px;
    left: 20px;
    max-width: 40vw;
}

.mensaje-esquina-superior-derecha {
    top: 20px;
    right: 20px;
    max-width: 40vw;
}

.mensaje-esquina-inferior-izquierda {
    bottom: 20px;
    left: 20px;
    max-width: 40vw;
}

.mensaje-esquina-inferior-derecha {
    bottom: 20px;
    right: 20px;
    max-width: 40vw;
}

/* Contador de intentos */
.contador-intentos {
    position: fixed;
    bottom: 20px;
    left: 20px;
    background: rgba(255,255,255,0.2);
    padding: 10px 20px;
    border-radius: 30px;
    color: white;
    font-size: 1.1em;
    backdrop-filter: blur(5px);
    z-index: 20;
    transition: opacity 0.5s ease;
}

/* Corazones flotantes */
.corazon-flotante {
    position: fixed;
    font-size: 25px;
    pointer-events: none;
    z-index: 1000;
    animation: flotarCorazon linear forwards;
}

@keyframes flotarCorazon {
    0% {
        transform: translateY(100vh) scale(1);
        opacity: 0.8;
    }
    100% {
        transform: translateY(-20vh) scale(1.5);
        opacity: 0;
    }
}

/* Corazones de la explosión */
.corazon-explosion {
    position: fixed;
    font-size: 30px;
    pointer-events: none;
    z-index: 1500;
    animation: explosionVuelo 2s ease-out forwards;
}

@keyframes explosionVuelo {
    0% {
        transform: translate(0, 0) scale(1) rotate(0deg);
        opacity: 1;
    }
    100% {
        transform: translate(var(--x), var(--y)) scale(1.5) rotate(var(--rotacion));
        opacity: 0;
    }
}

/* Indicador de progreso */
.progreso-container {
    position: fixed;
    top: 20px;
    right: 20px;
    background: rgba(255,255,255,0.2);
    padding: 15px 25px;
    border-radius: 50px;
    color: white;
    font-size: 1.3em;
    backdrop-filter: blur(5px);
    z-index: 20;
    border: 2px solid white;
    transition: opacity 0.5s ease;
}

.barra-progreso {
    width: 200px;
    height: 20px;
    background: rgba(255,255,255,0.3);
    border-radius: 10px;
    margin-top: 10px;
    overflow: hidden;
}

.progreso-llenado {
    height: 100%;
    width: 0%;
    background: linear-gradient(90deg, #ff4d6d, #ff1e4d);
    border-radius: 10px;
    transition: width 0.5s ease;
}

/* Zona segura central - área donde NO aparecerán mensajes */
.zona-segura-central {
    position: fixed;
    top: 30%;
    left: 30%;
    width: 40%;
    height: 40%;
    pointer-events: none;
    z-index: 1;
}
</style>
</head>

<body>

<!-- Zona segura invisible para referencia -->
<div class="zona-segura-central"></div>

<h1>💖 ¡Feliz Primer San Valentín! 💖</h1>

<div class="pregunta">¿Quieres ser mi Valentín? 👉👈</div>

<div class="botones">
    <button id="si">¡SÍ, CLARO! 💘</button>
    <button id="no">No 😢</button>
</div>

<!-- Contador de intentos -->
<div class="contador-intentos" id="contadorIntentos">
    Intentos con el No: <span id="intentosNo">0/5</span>
</div>

<!-- Indicador de progreso -->
<div class="progreso-container">
    <div>Progreso del amor ❤️</div>
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
const zonaSegura = document.querySelector('.zona-segura-central');

// Variables
let intentosNo = 0;
const MAX_INTENTOS = 5;
let crecimientoActivo = false;
let escalaActual = 1;
let mensajesActivos = 0;
const MAX_MENSAJES_SIMULTANEOS = 4;
const mensajesBorde = [
    "¡Ya casi dices que sí! 💕",
    "¡El amor crece! 💘",
    "¡Un paso más! 💖",
    "¡Sí, sí, SÍ! 💓",
    "¡No te rindas! 💗",
    "¡El destino nos une! ✨",
    "¡5 intentos y no podrás negarte! 💝",
    "¡Cada NO te acerca al SÍ! 💞",
    "¡El amor es más fuerte! 💪❤️",
    "¡Tu amor es inevitable! 💕",
    "¡Corazón contento! 🥰",
    "¡Eres especial! 💖"
];

// Función para verificar si una posición está en zona segura
function estaEnZonaSegura(x, y) {
    const zonaRect = {
        left: window.innerWidth * 0.2,
        right: window.innerWidth * 0.8,
        top: window.innerHeight * 0.2,
        bottom: window.innerHeight * 0.8
    };
    
    return (x > zonaRect.left && x < zonaRect.right && y > zonaRect.top && y < zonaRect.bottom);
}

// Función para verificar si un mensaje se superpone con el botón Sí
function seSuperponeConBotonSi(x, y, ancho, alto) {
    const botonRect = botonSi.getBoundingClientRect();
    
    // Si el botón es muy grande, considerar solo su posición central
    if (escalaActual > 3) {
        const centroBotonX = botonRect.left + botonRect.width / 2;
        const centroBotonY = botonRect.top + botonRect.height / 2;
        const distancia = Math.sqrt(Math.pow(x - centroBotonX, 2) + Math.pow(y - centroBotonY, 2));
        return distancia < 200; // Si está muy cerca del centro del botón grande
    }
    
    // Para botón normal, verificar superposición de rectángulos
    return !(x + ancho < botonRect.left || 
             x > botonRect.right || 
             y + alto < botonRect.top || 
             y > botonRect.bottom);
}

// Función para mostrar el mensaje central "yo también, tiamo"
function mostrarMensajeCentral() {
    // Crear el mensaje central
    const mensajeCentral = document.createElement('div');
    mensajeCentral.className = 'mensaje-central';
    
    // Dividir el mensaje en letras para animación
    const texto = "💕 yo también, tiamo 💕";
    for (let letra of texto) {
        const span = document.createElement('span');
        span.textContent = letra;
        mensajeCentral.appendChild(span);
    }
    
    document.body.appendChild(mensajeCentral);
    
    // Poner la página roja
    body.classList.add('rojo');
    
    // Ocultar elementos originales
    document.querySelector('h1').style.opacity = '0';
    document.querySelector('.pregunta').style.opacity = '0';
    document.querySelector('.botones').style.opacity = '0';
    document.querySelector('.contador-intentos').style.opacity = '0';
    document.querySelector('.progreso-container').style.opacity = '0';
    
    // Explosión masiva de corazones
    explosionMasivaCorazones();
    
    // Lluvia continua de corazones
    setInterval(() => {
        if (body.classList.contains('rojo')) {
            crearLluviaCorazones();
        }
    }, 500);
}

// Función para explosión masiva de corazones
function explosionMasivaCorazones() {
    const emojis = ['❤️', '💖', '💘', '💝', '💕', '💞', '💓', '💗', '💟', '❣️', '💔', '❤️‍🔥'];
    
    for (let i = 0; i < 200; i++) {
        setTimeout(() => {
            for (let j = 0; j < 3; j++) {
                const corazon = document.createElement('div');
                corazon.innerHTML = emojis[Math.floor(Math.random() * emojis.length)];
                corazon.style.position = 'fixed';
                corazon.style.left = (Math.random() * window.innerWidth) + 'px';
                corazon.style.top = (Math.random() * window.innerHeight) + 'px';
                corazon.style.fontSize = (20 + Math.random() * 50) + 'px';
                corazon.style.pointerEvents = 'none';
                corazon.style.zIndex = '1000';
                corazon.style.filter = 'drop-shadow(0 0 10px gold)';
                corazon.style.animation = 'aparecer 0.5s ease-out';
                
                document.body.appendChild(corazon);
                
                const angulo = Math.random() * Math.PI * 2;
                const distancia = 100 + Math.random() * 200;
                const x = Math.cos(angulo) * distancia;
                const y = Math.sin(angulo) * distancia;
                
                corazon.animate([
                    { transform: 'translate(0, 0) scale(1)', opacity: 1 },
                    { transform: `translate(${x}px, ${y}px) scale(1.5)`, opacity: 0 }
                ], {
                    duration: 2000,
                    easing: 'ease-out'
                });
                
                setTimeout(() => corazon.remove(), 2000);
            }
        }, i * 20);
    }
}

// Función para crear lluvia de corazones
function crearLluviaCorazones() {
    const emojis = ['❤️', '💖', '💘', '💝', '💕', '💞', '💓', '💗'];
    
    for (let i = 0; i < 10; i++) {
        setTimeout(() => {
            const corazon = document.createElement('div');
            corazon.innerHTML = emojis[Math.floor(Math.random() * emojis.length)];
            corazon.style.position = 'fixed';
            corazon.style.left = Math.random() * 100 + 'vw';
            corazon.style.top = '-50px';
            corazon.style.fontSize = (20 + Math.random() * 40) + 'px';
            corazon.style.pointerEvents = 'none';
            corazon.style.zIndex = '900';
            corazon.style.filter = 'drop-shadow(0 0 5px white)';
            
            document.body.appendChild(corazon);
            
            const duracion = 3 + Math.random() * 3;
            const rotacion = Math.random() * 360;
            
            corazon.animate([
                { transform: `translateY(0) rotate(0deg)`, opacity: 1 },
                { transform: `translateY(120vh) rotate(${rotacion}deg)`, opacity: 0.5 }
            ], {
                duration: duracion * 1000,
                easing: 'linear'
            });
            
            setTimeout(() => corazon.remove(), duracion * 1000);
        }, i * 100);
    }
}

// Evento click en botón SÍ
botonSi.addEventListener("click", () => {
    mostrarMensajeCentral();
});

// Función para actualizar barra de progreso
function actualizarProgreso() {
    const progreso = (intentosNo / MAX_INTENTOS) * 100;
    barraProgreso.style.width = progreso + '%';
    intentosSpan.textContent = intentosNo + '/' + MAX_INTENTOS;
    
    if (intentosNo >= MAX_INTENTOS - 1) {
        barraProgreso.style.background = 'linear-gradient(90deg, #ffd700, #ffa500)';
    }
}

// Función para crear mensajes en los bordes (EVITANDO EL CENTRO Y EL BOTÓN SÍ)
function crearMensajeEnBorde() {
    if (mensajesActivos >= MAX_MENSAJES_SIMULTANEOS) return;
    
    mensajesActivos++;
    
    // Elegir posición aleatoria entre las opciones (excluyendo el centro)
    const posiciones = [
        'arriba', 'abajo', 'izquierda', 'derecha',
        'esquina-superior-izquierda', 'esquina-superior-derecha',
        'esquina-inferior-izquierda', 'esquina-inferior-derecha'
    ];
    
    // Filtrar posiciones según el tamaño del botón Sí
    let posicionesDisponibles = [...posiciones];
    
    // Si el botón Sí es muy grande, evitar posiciones que puedan superponerse
    if (escalaActual > 5) {
        // Solo usar esquinas cuando el botón es enorme
        posicionesDisponibles = [
            'esquina-superior-izquierda', 'esquina-superior-derecha',
            'esquina-inferior-izquierda', 'esquina-inferior-derecha'
        ];
    } else if (escalaActual > 3) {
        // Evitar posiciones laterales si el botón es mediano
        posicionesDisponibles = posiciones.filter(p => 
            p.includes('esquina') || p === 'arriba' || p === 'abajo'
        );
    }
    
    const posicion = posicionesDisponibles[Math.floor(Math.random() * posicionesDisponibles.length)];
    
    const mensaje = document.createElement('div');
    mensaje.className = `mensaje-borde mensaje-${posicion}`;
    
    if (intentosNo === MAX_INTENTOS - 1) {
        mensaje.textContent = "¡ÚLTIMO INTENTO! 💘";
    } else {
        mensaje.textContent = mensajesBorde[Math.floor(Math.random() * mensajesBorde.length)];
    }
    
    const emojis = ['❤️', '💖', '💘', '💝', '💕', '💞', '💓', '💗'];
    mensaje.textContent += ' ' + emojis[Math.floor(Math.random() * emojis.length)];
    
    document.body.appendChild(mensaje);
    
    // Verificar superposición después de agregar
    setTimeout(() => {
        const rect = mensaje.getBoundingClientRect();
        if (seSuperponeConBotonSi(rect.left, rect.top, rect.width, rect.height)) {
            // Si se superpone, moverlo a una esquina
            mensaje.className = 'mensaje-borde mensaje-esquina-superior-izquierda';
        }
    }, 10);
    
    // Eliminar después de 3 segundos
    setTimeout(() => {
        mensaje.style.animation = 'aparecerMensaje 0.5s reverse';
        setTimeout(() => {
            mensaje.remove();
            mensajesActivos--;
        }, 500);
    }, 3000);
}

// Función para agrandar el botón Sí
function agrandarBotonSi() {
    if (!crecimientoActivo) {
        crecimientoActivo = true;
        botonSi.classList.add('creciendo');
    }
    
    escalaActual = 1 + (intentosNo * 0.8);
    botonSi.style.transform = `scale(${escalaActual})`;
    botonSi.style.zIndex = 1000 - intentosNo;
    
    const rect = botonSi.getBoundingClientRect();
    const windowWidth = window.innerWidth;
    const windowHeight = window.innerHeight;
    
    const leftPos = (windowWidth / 2) - (rect.width * escalaActual / 2);
    const topPos = (windowHeight / 2) - (rect.height * escalaActual / 2);
    
    botonSi.style.left = leftPos + 'px';
    botonSi.style.top = topPos + 'px';
    botonSi.style.position = 'fixed';
    
    // Crear menos mensajes si el botón ya es grande
    const numMensajes = escalaActual > 5 ? 1 : 2;
    for (let i = 0; i < numMensajes; i++) {
        setTimeout(() => {
            crearMensajeEnBorde();
        }, i * 300);
    }
    
    crearCorazonesAlrededor();
    
    if (intentosNo >= MAX_INTENTOS) {
        taparBotonNo();
    }
}

// Función para tapar el botón No
function taparBotonNo() {
    botonNo.classList.add('oculto');
    botonSi.style.transform = 'translate(-50%, -50%) scale(15)';
    botonSi.style.left = '50%';
    botonSi.style.top = '50%';
    botonSi.style.zIndex = '2000';
    
    setTimeout(() => {
        mostrarMensajeCentral();
    }, 500);
    
    // Crear mensajes solo en esquinas para la transición final
    for (let i = 0; i < 4; i++) {
        setTimeout(() => {
            const posiciones = ['esquina-superior-izquierda', 'esquina-superior-derecha', 
                               'esquina-inferior-izquierda', 'esquina-inferior-derecha'];
            const mensaje = document.createElement('div');
            mensaje.className = `mensaje-borde mensaje-${posiciones[i]}`;
            mensaje.textContent = "¡TE AMO! 💕";
            document.body.appendChild(mensaje);
            
            setTimeout(() => mensaje.remove(), 3000);
        }, i * 200);
    }
}

// Función para crear corazones alrededor
function crearCorazonesAlrededor() {
    const rect = botonSi.getBoundingClientRect();
    const centroX = rect.left + rect.width / 2;
    const centroY = rect.top + rect.height / 2;
    
    // Reducir cantidad de corazones si el botón es grande
    const cantidad = intentosNo === MAX_INTENTOS ? 10 : (escalaActual > 5 ? 5 : 10);
    
    for (let i = 0; i < cantidad; i++) {
        setTimeout(() => {
            for (let j = 0; j < 2; j++) {
                const angulo = Math.random() * Math.PI * 2;
                const distancia = 100 + Math.random() * (escalaActual > 5 ? 300 : 200);
                const x = centroX + Math.cos(angulo) * distancia;
                const y = centroY + Math.sin(angulo) * distancia;
                
                crearCorazon(x, y);
            }
        }, i * 50);
    }
}

// Función para crear un corazón
function crearCorazon(x, y) {
    const corazon = document.createElement('div');
    corazon.innerHTML = ['❤️', '💖', '💘', '💝', '💕', '💞', '💓', '💗'][Math.floor(Math.random() * 8)];
    corazon.style.position = 'fixed';
    corazon.style.left = x + 'px';
    corazon.style.top = y + 'px';
    corazon.style.fontSize = (20 + Math.random() * 40) + 'px';
    corazon.style.pointerEvents = 'none';
    corazon.style.zIndex = '500';
    corazon.style.animation = 'aparecer 0.8s ease-out';
    corazon.style.filter = 'drop-shadow(0 0 5px hotpink)';
    
    document.body.appendChild(corazon);
    
    corazon.animate([
        { transform: 'translateY(0px) rotate(0deg)', opacity: 1 },
        { transform: `translateY(-${80 + Math.random() * 100}px) rotate(${Math.random() * 360}deg)`, opacity: 0 }
    ], {
        duration: 2000,
        easing: 'ease-out'
    });
    
    setTimeout(() => corazon.remove(), 2000);
}

// Evento click en botón No
botonNo.addEventListener("click", (e) => {
    e.preventDefault();
    e.stopPropagation();
    
    if (intentosNo < MAX_INTENTOS) {
        intentosNo++;
        actualizarProgreso();
        agrandarBotonSi();
        
        for (let i = 0; i < 5; i++) {
            setTimeout(() => {
                crearCorazon(
                    e.clientX + (Math.random() - 0.5) * 150,
                    e.clientY + (Math.random() - 0.5) * 150
                );
            }, i * 50);
        }
        
        if (intentosNo === MAX_INTENTOS) {
            setTimeout(() => {
                crearMensajeEnBorde();
            }, 500);
        }
    }
    
    return false;
});

// Posicionar botones inicialmente
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
    
    setInterval(() => {
        if (!body.classList.contains('rojo') && Math.random() > 0.7) {
            crearCorazon(
                Math.random() * window.innerWidth,
                Math.random() * window.innerHeight
            );
        }
    }, 2000);
});

// Actualizar al cambiar tamaño
window.addEventListener('resize', () => {
    if (!crecimientoActivo) {
        posicionarBotones();
    }
});
</script>

</body>
</html>
