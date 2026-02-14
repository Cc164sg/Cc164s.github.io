# Cc164s.github.io
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
}

/* Fondo ositos mejorado */
body::before {
    content: "🐻 💖 🐻 💕 🐻 💘 🐻 💞 🐻 💓 🐻 💗 🐻 💝";
    font-size: 80px;
    position: fixed;
    width: 300%;
    height: 300%;
    opacity: 0.1;
    animation: mover 45s linear infinite;
    white-space: nowrap;
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
}

.botones {
    margin-top: 40px;
    position: relative;
    width: 400px;
    height: 180px;
    z-index: 10;
}

button {
    padding: 18px 45px;
    font-size: 1.4em;
    font-weight: bold;
    border: none;
    border-radius: 50px;
    cursor: pointer;
    position: absolute;
    transition: all 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
    box-shadow: 0 4px 15px rgba(0,0,0,0.2);
}

#si {
    background: linear-gradient(45deg, #ff4d6d, #ff1e4d);
    color: white;
    left: 5%;
    transition: all 0.3s ease;
}

#si:hover {
    transform: scale(1.1);
    box-shadow: 0 0 30px #ff4d6d;
}

#no {
    background: linear-gradient(45deg, #6b6b6b, #4a4a4a);
    color: white;
    right: 5%;
    cursor: not-allowed;
    opacity: 0.9;
}

#no:hover {
    background: linear-gradient(45deg, #7a7a7a, #5a5a5a);
}

.mensajeFinal {
    font-size: 4em;
    color: #fff;
    text-shadow: 3px 3px 6px #ff006e;
    margin-top: 30px;
    display: none;
    z-index: 10;
    animation: aparecer 1s ease-out;
}

@keyframes aparecer {
    0% { opacity: 0; transform: scale(0.5); }
    100% { opacity: 1; transform: scale(1); }
}

/* Corazones flotantes mejorados */
.corazon-flotante {
    position: fixed;
    font-size: 25px;
    pointer-events: none;
    z-index: 5;
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

/* Corazones explosión mejorados */
.explosion-corazon {
    position: fixed;
    font-size: 30px;
    pointer-events: none;
    z-index: 1000;
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
}

/* Mensaje especial después de varios intentos */
.mensaje-especial {
    position: fixed;
    bottom: 80px;
    left: 20px;
    background: rgba(255,255,255,0.3);
    padding: 15px 25px;
    border-radius: 30px;
    color: white;
    font-size: 1.2em;
    backdrop-filter: blur(5px);
    z-index: 20;
    animation: mensajeAparecer 0.5s ease-out;
}

@keyframes mensajeAparecer {
    from { opacity: 0; transform: translateX(-50px); }
    to { opacity: 1; transform: translateX(0); }
}
</style>
</head>

<body>

<h1>💖 ¡Feliz Primer San Valentín! 💖</h1>

<div class="pregunta">¿Quieres ser mi Valentín? 👉👈</div>

<div class="botones">
    <button id="si">¡SÍ, CLARO! 💘</button>
    <button id="no">No 😢</button>
</div>

<div class="mensajeFinal" id="mensajeFinal">
    💕 ¡YO TAMBIÉN, TE AMO! 💕
</div>

<!-- Contador de intentos -->
<div class="contador-intentos" id="contadorIntentos">
    Intentos con el No: <span id="intentosNo">0</span>
</div>

<script>
// Elementos del DOM
const botonNo = document.getElementById("no");
const botonSi = document.getElementById("si");
const mensajeFinal = document.getElementById("mensajeFinal");
const intentosSpan = document.getElementById("intentosNo");

// Variables
let intentosNo = 0;
let tiempoUltimoMovimiento = 0;
const mensajesDivertidos = [
    "¡No puedes escapar de mi amor! 💕",
    "¡El amor es más fuerte! 💪❤️",
    "¡Nunca digas No en San Valentín! 😊",
    "¡Inténtalo de nuevo! 🥺",
    "¡Mi corazón te persigue! 🏃‍♂️❤️",
    "¡El destino quiere que digas Sí! ✨",
    "¡No te rindas, di Sí! 🌹",
    "¡El amor siempre gana! 🏆❤️"
];

// Posición inicial del botón No
function posicionarBotonNo() {
    const contenedor = document.querySelector('.botones');
    const contenedorRect = contenedor.getBoundingClientRect();
    
    botonNo.style.position = "absolute";
    botonNo.style.left = "60%";
    botonNo.style.top = "40%";
}

posicionarBotonNo();

// Función mejorada para que el botón No escape
function escaparBotonNo(event) {
    const rect = botonNo.getBoundingClientRect();
    const mouseX = event.clientX;
    const mouseY = event.clientY;
    
    // Calcular centro del botón
    const centroX = rect.left + rect.width / 2;
    const centroY = rect.top + rect.height / 2;
    
    // Calcular distancia
    const distanciaX = mouseX - centroX;
    const distanciaY = mouseY - centroY;
    const distancia = Math.sqrt(distanciaX * distanciaX + distanciaY * distanciaY);
    
    // Si el mouse está cerca (180px), el botón escapa
    if (distancia < 180) {
        
        // Incrementar contador de intentos
        intentosNo++;
        intentosSpan.textContent = intentosNo;
        
        // Mostrar mensaje divertido cada 3 intentos
        if (intentosNo % 3 === 0) {
            mostrarMensajeDivertido();
        }
        
        // Crear pequeño corazón al intentar hacer clic en No
        crearCorazonPersecucion(mouseX, mouseY);
        
        // Calcular dirección de escape (opuesta al mouse)
        let nuevaX = rect.left - (distanciaX * 2);
        let nuevaY = rect.top - (distanciaY * 2);
        
        // Limitar dentro de la ventana
        nuevaX = Math.max(10, Math.min(window.innerWidth - rect.width - 10, nuevaX));
        nuevaY = Math.max(10, Math.min(window.innerHeight - rect.height - 10, nuevaY));
        
        // Aplicar nueva posición
        botonNo.style.left = nuevaX + "px";
        botonNo.style.top = nuevaY + "px";
        botonNo.style.transition = "left 0.2s ease, top 0.2s ease";
        
        // Hacer que el botón parpadee
        botonNo.style.animation = "none";
        botonNo.offsetHeight; // Forzar reflow
        botonNo.style.animation = "latido 0.3s ease";
        
        tiempoUltimoMovimiento = Date.now();
    }
}

// Mostrar mensaje divertido
function mostrarMensajeDivertido() {
    const mensajeDivertido = document.createElement('div');
    mensajeDivertido.className = 'mensaje-especial';
    mensajeDivertido.textContent = mensajesDivertidos[Math.floor(Math.random() * mensajesDivertidos.length)];
    
    document.body.appendChild(mensajeDivertido);
    
    setTimeout(() => {
        mensajeDivertido.remove();
    }, 3000);
}

// Crear corazón donde el mouse intentó hacer clic en No
function crearCorazonPersecucion(x, y) {
    const corazon = document.createElement('div');
    corazon.innerHTML = '💖';
    corazon.style.position = 'fixed';
    corazon.style.left = x + 'px';
    corazon.style.top = y + 'px';
    corazon.style.fontSize = '25px';
    corazon.style.pointerEvents = 'none';
    corazon.style.zIndex = '1000';
    corazon.style.animation = 'aparecer 0.5s ease-out';
    
    document.body.appendChild(corazon);
    
    setTimeout(() => corazon.remove(), 500);
}

// Evento mousemove para que el botón No escape
document.addEventListener("mousemove", escaparBotonNo);

// Prevenir que el botón No reciba clics
botonNo.addEventListener("click", (e) => {
    e.preventDefault();
    e.stopPropagation();
    
    // Crear corazón extra
    for (let i = 0; i < 5; i++) {
        setTimeout(() => {
            crearCorazonPersecucion(
                e.clientX + (Math.random() - 0.5) * 100,
                e.clientY + (Math.random() - 0.5) * 100
            );
        }, i * 50);
    }
    
    return false;
});

// Función mejorada de explosión de corazones
function explosionCorazones() {
    const centroX = window.innerWidth / 2;
    const centroY = window.innerHeight / 2;
    const emojis = ['❤️', '💖', '💘', '💝', '💕', '💞', '💓', '💗', '💟'];
    
    for (let i = 0; i < 120; i++) {
        let corazon = document.createElement("div");
        corazon.innerHTML = emojis[Math.floor(Math.random() * emojis.length)];
        corazon.className = "explosion-corazon";
        corazon.style.left = centroX + "px";
        corazon.style.top = centroY + "px";
        
        let angulo = Math.random() * 2 * Math.PI;
        let distancia = Math.random() * 400 + 100;
        let rotacion = Math.random() * 360;
        let escala = 0.5 + Math.random() * 1.5;
        
        let x = Math.cos(angulo) * distancia;
        let y = Math.sin(angulo) * distancia;
        
        document.body.appendChild(corazon);
        
        corazon.animate([
            { 
                transform: `translate(0, 0) scale(1) rotate(0deg)`,
                opacity: 1 
            },
            { 
                transform: `translate(${x}px, ${y}px) scale(${escala}) rotate(${rotacion}deg)`,
                opacity: 0 
            }
        ], {
            duration: 2000,
            easing: "cubic-bezier(0.25, 0.1, 0.25, 1)"
        });
        
        setTimeout(() => corazon.remove(), 2000);
    }
}

// Función mejorada de lluvia de corazones
function lluviaCorazones() {
    const emojis = ['❤️', '💖', '💘', '💝', '💕', '💞', '💓', '💗', '💟'];
    
    for (let i = 0; i < 200; i++) {
        setTimeout(() => {
            let corazon = document.createElement("div");
            corazon.innerHTML = emojis[Math.floor(Math.random() * emojis.length)];
            corazon.className = "corazon-flotante";
            corazon.style.left = Math.random() * 100 + "vw";
            corazon.style.fontSize = (15 + Math.random() * 30) + "px";
            
            let duracion = Math.random() * 4 + 3;
            
            document.body.appendChild(corazon);
            
            corazon.animate([
                { 
                    transform: `translateY(100vh) scale(${0.5 + Math.random()})`,
                    opacity: 0.8 
                },
                { 
                    transform: `translateY(-20vh) scale(${1.5 + Math.random()})`,
                    opacity: 0 
                }
            ], {
                duration: duracion * 1000,
                easing: "linear"
            });
            
            setTimeout(() => corazon.remove(), duracion * 1000);
        }, i * 20); // Espaciado para efecto cascada
    }
}

// Cuando presiona SÍ - versión mejorada
botonSi.addEventListener("click", () => {
    // Mostrar mensaje
    mensajeFinal.style.display = "block";
    
    // Ocultar botones
    document.querySelector('.botones').style.opacity = '0';
    document.querySelector('.botones').style.pointerEvents = 'none';
    
    // Ocultar contador
    document.querySelector('.contador-intentos').style.opacity = '0';
    
    // Explosión principal
    explosionCorazones();
    
    // Lluvia continua
    lluviaCorazones();
    
    // Segunda explosión después de 1 segundo
    setTimeout(() => explosionCorazones(), 1000);
    
    // Tercera explosión después de 2 segundos
    setTimeout(() => explosionCorazones(), 2000);
    
    // Crear corazones alrededor del mensaje
    let contadorMensaje = 0;
    const intervaloMensaje = setInterval(() => {
        if (contadorMensaje < 10) {
            const rect = mensajeFinal.getBoundingClientRect();
            if (rect.top) {
                crearCorazonPersecucion(
                    rect.left + rect.width / 2 + (Math.random() - 0.5) * 200,
                    rect.top + rect.height / 2 + (Math.random() - 0.5) * 200
                );
            }
            contadorMensaje++;
        } else {
            clearInterval(intervaloMensaje);
        }
    }, 200);
});

// Ajustar posición al cambiar tamaño de ventana
window.addEventListener('resize', () => {
    if (mensajeFinal.style.display !== 'block') {
        posicionarBotonNo();
    }
});

// Agregar corazones de fondo aleatorios
setInterval(() => {
    if (mensajeFinal.style.display !== 'block') {
        crearCorazonPersecucion(
            Math.random() * window.innerWidth,
            Math.random() * window.innerHeight
        );
    }
}, 2000);

console.log("¡Feliz San Valentín! ❤️");
</script>

</body>
</html>
