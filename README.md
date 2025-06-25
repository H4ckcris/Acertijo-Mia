[<meta name='viewport' content='width=device-width, initial-scale=1'/><!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Acertijos de Amor: Para Sandra y Mía Guadalupe</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Pacifico&family=Quicksand:wght@300;400;500;700&display=swap" rel="stylesheet">
    <link rel="icon" type="image/png" href="https://upload.wikimedia.wikimedia.org/wikipedia/commons/thumb/4/42/Love_Heart_SVG.svg/1200px-Love_Heart_SVG.svg.png">
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <button id="hamburgerMenuBtn" aria-label="Menú de ayuda">
        <div class="bar"></div>
        <div class="bar"></div>
        <div class="bar"></div>
    </button>
    <div id="hamburgerMenu" class="hidden">
        <h3>¿Necesitan Ayuda?</h3>
        <ul>
            <li id="getHint">¿Pista para el acertijo actual? 💡</li>
            <li id="creativeThinking">Desbloquear el Pensamiento Creativo 🧠</li>
            <li id="riddleTypes">Tipos de Acertijos 📚</li>
            <li id="strongHint">Pista Súper Secreta 🤫</li>
            <li id="showAnswer" class="disabled-option">¡Trampa con amor! (Ver respuesta) 🙈</li>
            <li id="contactDad">Pedir Ayuda a Papá Cristian🥰<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/6/6b/WhatsApp.svg/1200px-WhatsApp.svg.png" alt="WhatsApp Icon" class="whatsapp-icon"></li>
        </ul>
    </div>

    <div id="passwordScreen">
        <div id="passwordImageContainer">
            <div id="passwordImage"></div>
            <div id="glitterOverlay"></div>
        </div>
        <h1>¡Hola, mis amores!</h1>
        <p>La clave de nuestro amor, ¡ingrésenla!</p>
        <div id="passwordContainer" class="interactive-password">
            <input type="password" id="passwordInput" maxlength="4" aria-label="Introduce la clave de amor">
            <div class="password-dots">
                <span class="dot"></span>
                <span class="dot"></span>
                <span class="dot"></span>
                <span class="dot"></span>
            </div>
        </div>
        <button id="passwordButton" aria-label="Verificar clave">¡Es la clave! ❤️</button>
        <p id="passwordError" class="hidden" aria-live="polite">¡Uhm... casi! Intentemos de nuevo.</p>
    </div>

    <div class="heart-rain" id="heartRainContainer"></div>

    <div class="container" id="gameContainer">
        <h1 id="title">Juego para las bonitas <span class="heart">💖</span></h1>
        <p class="subtitle">¡Una Sorpresa para Sandra y Mía Guadalupe!</p>
        <p id="description">Mis amores, he preparado estos acertijos especiales para ustedes. ¡Cada respuesta correcta es un paso más cerca de una sorpresa!</p>

        <div id="riddleDisplay">
            <p id="riddleTarget">¡Este acertijo es para <span id="riddleFor"></span>!</p>
            <p id="riddleText">Cargando acertijo...</p>
            <input type="text" id="riddleInput" placeholder="¡Escriban su respuesta con amor!" aria-label="Escriban su respuesta del acertijo aquí">
            <button id="submitRiddle" aria-label="Resolver acertijo">¡Resolver con el Corazón! ❤️</button>
            <p id="riddleFeedback" aria-live="polite"></p>
        </div>

        <div id="finalMessage" class="hidden">
            <h2>¡Lo lograron, mis ingeniosas princesas! 🎉</h2>
            <p>Han resuelto todos los acertijos con su amor, ingenio y el brillo único de cada una.</p>
            <p>Este es solo el comienzo de nuestra sorpresa. ¡El amor es el código secreto que lo abre todo!</p>
            <p id="hiddenMessage">"Su amor ilumina mi mundo cada día. Gracias por ser las mejores."</p>

            <p>Y ahora, la sorpresa final... ¡Un **vale de amor** para una aventura especial!</p>
            <div class="surprise-ticket">
                🎉 ¡Vale por un día de diversión sorpresa elegido por ustedes! 🎉
            </div>
            <button id="restartButton" aria-label="Volver a empezar el juego">Volver a Empezar ✨</button>
        </div>
    </div>
    <div class="fireworks-container" id="fireworksContainer"></div>

    <script src="script.js"></script>
</body>
</html>
<style>:root {
    --primary-pink: #FF69B4; /* Rosa Vibrante */
    --light-pink: #FFC0CB; /* Rosa Claro */
    --soft-purple: #B19CD9; /* Lavanda Suave */
    --accent-yellow: #FFD700; /* Dorado */
    --dark-text: #5A3D7D; /* Morado Oscuro */
    --background-start: #f8c0e2; /* Rosa claro personalizado para degradado */
    --background-end: #c0f8e2; /* Verde claro personalizado para degradado */
}

body {
    font-family: 'Quicksand', sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    background: linear-gradient(135deg, var(--background-start), var(--background-end)); /* Degradado suave moderno */
    color: var(--dark-text);
    margin: 0;
    padding: 20px;
    box-sizing: border-box;
    text-align: center;
    position: relative;
    overflow: hidden; /* Evita barras de desplazamiento por lluvia de corazones y fuegos artificiales */
}

/* --- Estilos del Menú de Hamburguesa --- */
#hamburgerMenuBtn {
    position: fixed; /* Cambiado a fixed para que se quede en la pantalla */
    top: 20px;
    left: 20px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    width: 30px;
    height: 22px;
    background: transparent;
    border: none;
    cursor: pointer;
    padding: 0;
    z-index: 100; /* Alto z-index para estar siempre encima */
}
.bar {
    width: 100%;
    height: 3px;
    background-color: var(--primary-pink);
    border-radius: 2px;
    transition: all 0.3s ease-in-out;
}
#hamburgerMenuBtn.open .bar:nth-child(1) {
    transform: rotate(45deg) translate(6px, 5px);
}
#hamburgerMenuBtn.open .bar:nth-child(2) {
    opacity: 0;
}
#hamburgerMenuBtn.open .bar:nth-child(3) {
    transform: rotate(-45deg) translate(6px, -5px);
}

#hamburgerMenu {
    position: fixed; /* Mantenido como fixed */
    top: 0;
    left: 0;
    width: 250px;
    height: 100%;
    background-color: rgba(255, 255, 255, 0.98);
    z-index: 99; /* Ligeramente por debajo del botón */
    padding: 80px 30px 30px 30px;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    transform: translateX(-100%);
    transition: transform 0.3s ease-in-out;
    box-shadow: 2px 0 10px rgba(0,0,0,0.1);
}
#hamburgerMenu.open {
    transform: translateX(0);
}
#hamburgerMenu h3 {
    font-family: 'Pacifico', cursive;
    color: var(--soft-purple);
    margin-bottom: 25px;
    font-size: 1.8em;
}
#hamburgerMenu ul {
    list-style: none;
    padding: 0;
    margin: 0;
    width: 100%;
}
#hamburgerMenu ul li {
    padding: 18px 0;
    border-bottom: 1px solid var(--light-pink);
    color: var(--dark-text);
    cursor: pointer;
    transition: background-color 0.3s ease, transform 0.2s ease;
    font-size: 1.1em;
    font-weight: 500;
    display: flex; /* Para alinear íconos y texto */
    align-items: center; /* Para centrar verticalmente */
    gap: 8px; /* Espacio entre ícono y texto */
}
#hamburgerMenu ul li:last-child {
    border-bottom: none;
}
#hamburgerMenu ul li:hover {
    background-color: rgba(255, 192, 203, 0.2);
    transform: translateX(5px);
}

/* Estilo para opciones deshabilitadas */
#hamburgerMenu ul li.disabled-option {
    color: #ccc; /* Color gris para indicar que está deshabilitado */
    cursor: not-allowed; /* Cursor de "no permitido" */
    opacity: 0.6; /* Un poco de transparencia */
    pointer-events: none; /* Evita que se pueda hacer clic */
}
#hamburgerMenu ul li.disabled-option:hover {
    background-color: transparent; /* No cambia de color al pasar el ratón */
    transform: none; /* No hay efecto de transformación */
}

/* Estilo para el ícono de WhatsApp */
.whatsapp-icon {
    width: 24px; /* Tamaño del ícono */
    height: 24px;
    vertical-align: middle; /* Alineación vertical con el texto */
    margin-left: 5px; /* Espacio a la izquierda del ícono */
}


/* --- Estilos de la Pantalla de Contraseña --- */
#passwordScreen {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(135deg, #FFDAB9, #FFC0CB);
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    z-index: 20;
    transition: opacity 1s ease-out;
    opacity: 1;
    overflow: hidden;
}
#passwordImageContainer {
    position: relative;
    width: 80%;
    max-width: 400px;
    height: 250px;
    border-radius: 20px;
    box-shadow: 0 10px 25px rgba(0,0,0,0.2);
    margin-bottom: 30px;
    animation: fadeInImage 1.5s ease-out;
    overflow: hidden;
    border: 3px solid var(--primary-pink);
}
#passwordImage {
    width: 100%;
    height: 100%;
    background-image: url('https://i.ibb.co/VpxcBYY1/90baf0e0-2c4e-4206-b90f-c1d77e5fb796.jpg'); /* REEMPLAZAR CON TU URL DE IMAGEN */
    background-size: cover;
    background-position: center;
    border-radius: 17px;
    position: absolute;
    top: 0;
    left: 0;
    z-index: 1;
    animation: panImage 10s infinite alternate;
}
@keyframes panImage {
    0% { background-position: 0% 50%; }
    100% { background-position: 100% 50%; }
}

/* Superposición de Brillo */
#glitterOverlay {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: radial-gradient(circle, transparent 1%, rgba(255,255,255,0.05) 1%, rgba(255,255,255,0.1) 2%, transparent 2.5%);
    background-size: 20px 20px;
    animation: glitter 10s linear infinite;
    z-index: 2;
}
@keyframes glitter {
    from { background-position: 0 0; }
    to { background-position: 200px 200px; }
}

/* Partículas de Polvo Mágico */
.magic-particle {
    position: absolute;
    background-color: rgba(255, 255, 255, 0.8);
    border-radius: 50%;
    animation: magicGlow 2s infinite alternate, floatParticle 10s infinite linear;
    box-shadow: 0 0 5px rgba(255, 255, 255, 0.7);
    z-index: 3;
    pointer-events: none;
}
@keyframes magicGlow {
    0% { opacity: 0.5; transform: scale(0.8); }
    50% { opacity: 1; transform: scale(1.2); }
    100% { opacity: 0.5; transform: scale(0.8); }
}
@keyframes floatParticle {
    0% { transform: translate(var(--startX), var(--startY)); }
    100% { transform: translate(var(--endX), var(--endY)); }
}

@keyframes fadeInImage {
    from { opacity: 0; transform: translateY(-20px); }
    to { opacity: 1; transform: translateY(0); }
}
#passwordScreen h1 {
    font-family: 'Pacifico', cursive;
    color: var(--primary-pink);
    font-size: 2.8em;
    margin-bottom: 15px;
    text-shadow: 2px 2px 8px rgba(255, 105, 180, 0.4);
}
#passwordScreen p {
    font-size: 1.1em;
    color: var(--dark-text);
    margin-bottom: 25px;
}
#passwordContainer {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-bottom: 20px;
    position: relative;
}
#passwordInput {
    position: absolute;
    width: 100%;
    height: 100%;
    opacity: 0;
    cursor: pointer;
    z-index: 5;
}
.password-dots {
    display: flex;
    gap: 15px;
    padding: 10px 0;
    border-radius: 10px;
    background-color: rgba(255, 255, 255, 0.7);
    box-shadow: 0 0 10px rgba(255,105,180,0.3);
}
.dot {
    width: 25px;
    height: 25px;
    border-radius: 50%;
    background-color: #ddd;
    border: 2px solid var(--light-pink);
    transition: background-color 0.3s ease, transform 0.2s ease;
    transform: scale(1);
}
.dot.filled {
    background-color: var(--primary-pink);
    transform: scale(1.1);
}
.dot.incorrect {
    animation: shake 0.5s;
    background-color: #e91e63;
}
@keyframes shake {
    0% { transform: translateX(0); }
    25% { transform: translateX(-5px); }
    50% { transform: translateX(5px); }
    75% { transform: translateX(-5px); }
    100% { transform: translateX(0); }
}


#passwordButton {
    background-color: var(--soft-purple);
    color: white;
    padding: 15px 30px;
    border-radius: 30px;
    font-size: 1.1em;
    cursor: pointer;
    border: none;
    box-shadow: 0 5px 15px rgba(177,156,217,0.4);
    transition: background-color 0.3s, transform 0.3s, box-shadow 0.3s;
    margin-top: 25px;
}
#passwordButton:hover {
    background-color: #9c7abe;
    transform: translateY(-3px);
}
#passwordButton:active {
    transform: translateY(-1px) scale(0.98);
    box-shadow: 0 2px 8px rgba(177,156,217,0.6);
}

#passwordError {
    color: #e91e63;
    margin-top: 10px;
    font-weight: bold;
}

/* --- Estilos del Contenedor del Juego (Inicialmente oculto) --- */
.container {
    background-color: rgba(255, 255, 255, 0.98);
    padding: 45px;
    border-radius: 30px;
    box-shadow: 0 15px 40px rgba(0, 0, 0, 0.15);
    max-width: 750px;
    width: 100%;
    transition: all 0.6s ease-in-out;
    border: 4px solid var(--primary-pink);
    z-index: 10;
    position: relative;
    animation: none;
    opacity: 0;
    pointer-events: none;
}
.container.visible {
    opacity: 1;
    pointer-events: auto;
    animation: bounceIn 1s ease-out;
}
@keyframes bounceIn {
    0% { transform: scale(0.8); opacity: 0; }
    60% { transform: scale(1.05); opacity: 1; }
    100% { transform: scale(1); }
}

h1 {
    font-family: 'Pacifico', cursive;
    color: var(--primary-pink);
    margin-bottom: 25px;
    font-size: 3.5em;
    text-shadow: 3px 3px 10px rgba(255, 105, 180, 0.4);
}
.subtitle {
    font-size: 1.1em;
    color: var(--soft-purple);
    margin-bottom: 30px;
}
p {
    font-size: 1.25em;
    line-height: 1.7;
    margin-bottom: 30px;
    color: var(--dark-text);
}
#riddleTarget {
    font-size: 1.3em;
    color: var(--soft-purple);
    margin-bottom: 10px;
    font-weight: 500;
}
#riddleTarget span {
    font-weight: 700;
    color: var(--primary-pink);
    text-shadow: 0 0 5px rgba(255,105,180,0.3);
}
#riddleText {
    font-size: 1.5em;
    margin-bottom: 35px;
    color: var(--dark-text);
    font-weight: 500;
}
#riddleInput {
    width: calc(100% - 60px);
    padding: 18px;
    margin-top: 25px;
    border-radius: 15px;
    border: 3px solid var(--light-pink);
    background-color: #fffaf0;
    font-size: 1.3em;
    text-align: center;
    font-family: 'Quicksand', sans-serif;
    color: var(--dark-text);
    box-shadow: 0 0 12px rgba(255, 192, 203, 0.4);
    outline: none;
    transition: border-color 0.3s ease, box-shadow 0.3s ease;
}
#riddleInput:focus {
    border-color: var(--primary-pink);
    box-shadow: 0 0 15px rgba(255, 105, 180, 0.6);
}
button {
    background-color: var(--primary-pink);
    color: white;
    border: none;
    padding: 20px 35px;
    margin: 20px 10px;
    border-radius: 35px;
    font-size: 1.3em;
    cursor: pointer;
    transition: background-color 0.3s ease, transform 0.3s ease, box-shadow 0.3s ease;
    box-shadow: 0 6px 20px rgba(255, 105, 180, 0.5);
    font-family: 'Quicksand', sans-serif;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 1px;
}
button:hover {
    background-color: #e64b98;
    transform: translateY(-7px) scale(1.02);
    box-shadow: 0 10px 25px rgba(255, 105, 180, 0.7);
}
button:active {
    transform: translateY(-4px) scale(0.98);
    box-shadow: 0 4px 10px rgba(255, 105, 180, 0.6);
}

#riddleFeedback {
    margin-top: 20px;
    font-weight: 700;
    font-size: 1.15em;
    color: var(--primary-pink);
    text-shadow: 0 0 8px rgba(255, 105, 180, 0.5);
    transition: color 0.3s, text-shadow 0.3s;
}
.hidden {
    display: none;
}
.heart {
    color: #ff4d94;
    font-size: 2em;
    animation: pulse 1.8s infinite alternate;
    text-shadow: 0 0 12px rgba(255, 77, 148, 0.8);
    user-select: none;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
}
@keyframes pulse {
    0% { transform: scale(1); }
    100% { transform: scale(1.25); }
}

/* Estilos de Lluvia de Corazones */
.heart-rain {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    pointer-events: none;
    overflow: hidden;
    z-index: 1;
}
.heart-rain span {
    position: absolute;
    font-size: 1.8em;
    color: var(--light-pink);
    animation: fall linear infinite, rotateHeart linear infinite;
    opacity: 0;
    text-shadow: 0 0 8px rgba(255, 192, 203, 0.8);
    user-select: none;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
}
@keyframes fall {
    0% {
        transform: translateY(-10vh) translateX(0);
        opacity: 0;
    }
    10% {
        opacity: 0.9;
    }
    100% {
        transform: translateY(100vh) translateX(var(--x-end));
        opacity: 0;
    }
}
@keyframes rotateHeart {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg); }
}

/* Estilos de Mensaje Final y Sorpresa */
#finalMessage {
    padding: 30px;
    border: 3px dashed var(--soft-purple);
    border-radius: 20px;
    background-color: #fffafa;
    margin-top: 40px;
    animation: fadeInScale 1.5s ease-out;
}
@keyframes fadeInScale {
    from { opacity: 0; transform: scale(0.8); }
    to { opacity: 1; transform: scale(1); }
}
#finalMessage h2 {
    font-family: 'Pacifico', cursive;
    color: var(--primary-pink);
    font-size: 2.8em;
    margin-bottom: 20px;
    text-shadow: 2px 2px 5px rgba(255, 105, 180, 0.3);
}
#finalMessage p {
    color: var(--dark-text);
    font-size: 1.3em;
    margin-bottom: 30px;
}
#hiddenMessage {
    font-family: 'Pacifico', cursive;
    font-size: 1.8em;
    color: var(--soft-purple);
    margin: 25px 0;
    animation: revealMessage 2s ease-out forwards;
    opacity: 0;
}
@keyframes revealMessage {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
}
.surprise-ticket {
    background-color: var(--accent-yellow);
    color: var(--dark-text);
    padding: 15px 25px;
    border-radius: 10px;
    font-weight: 700;
    font-size: 1.1em;
    margin-top: 30px;
    display: inline-block;
    box-shadow: 0 5px 15px rgba(255, 215, 0, 0.5);
    animation: pulseTicket 1.5s infinite alternate;
}
@keyframes pulseTicket {
    0% { transform: scale(1); box-shadow: 0 5px 15px rgba(255, 215, 0, 0.5); }
    100% { transform: scale(1.05); box-shadow: 0 8px 20px rgba(255, 215, 0, 0.8); }
}

/* Animación de Fuegos Artificiales */
.fireworks-container {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    pointer-events: none;
    z-index: 100;
}
.firework {
    position: absolute;
    width: 10px;
    height: 10px;
    background-color: #fff;
    border-radius: 50%;
    opacity: 0;
    animation: firework 2s forwards ease-out;
    box-shadow: 0 0 10px rgba(255,255,255,0.8);
}
@keyframes firework {
    0% { transform: translate(var(--x-start), var(--y-start)) scale(0); opacity: 0; }
    20% { transform: translate(var(--x-mid), var(--y-mid)) scale(1); opacity: 1; }
    100% { transform: translate(var(--x-end), var(--y-end)) scale(0.5); opacity: 0; }
}

@keyframes explodeParticle {
    0% { transform: translate(0, 0) scale(0); opacity: 1; }
    50% { transform: translate(var(--endX), var(--endY)) scale(1); opacity: 1; }
    100% { transform: translate(var(--endX), var(--endY)) scale(0); opacity: 0; }
}

/* --- Media Queries para Diseño Responsivo --- */
@media (max-width: 768px) {
    body {
        padding: 10px;
    }
    .container, #passwordScreen {
        padding: 25px;
    }
    h1 {
        font-size: 2.5em;
    }
    #passwordScreen h1 {
        font-size: 2em;
    }
    p, #riddleTarget, #riddleText {
        font-size: 1em;
    }
    #riddleInput {
        padding: 12px;
        font-size: 1em;
    }
    .password-dots {
        gap: 10px;
    }
    .dot {
        width: 18px;
        height: 18px;
    }
    button {
        padding: 15px 25px;
        font-size: 1em;
    }
    #passwordImageContainer {
        height: 180px;
    }
    #finalMessage h2 {
        font-size: 2em;
    }
    #finalMessage p {
        font-size: 1em;
    }
    #hiddenMessage {
        font-size: 1.4em;
    }
    .surprise-ticket {
        font-size: 0.9em;
        padding: 12px 20px;
    }
    #hamburgerMenuBtn {
        top: 15px;
        left: 15px;
    }
    #hamburgerMenu {
        width: 180px;
        padding: 20px;
        padding-top: 60px;
    }
    #hamburgerMenu ul li {
        padding: 10px 0;
        font-size: 0.95em; /* Ajuste de tamaño de fuente para dispositivos pequeños */
    }
    .whatsapp-icon {
        width: 20px; /* Tamaño más pequeño para el ícono en móviles */
        height: 20px;
    }
}

@media (max-width: 480px) {
    h1 {
        font-size: 2em;
    }
    #passwordScreen h1 {
        font-size: 1.8em;
    }
    .subtitle {
        font-size: 0.9em;
    }
    button {
        margin: 10px 5px;
        padding: 12px 20px;
    }
    #riddleInput {
        padding: 10px;
        font-size: 0.9em;
    }
    .password-dots {
        gap: 8px;
    }
    .dot {
        width: 15px;
        height: 15px;
    }
    #passwordImageContainer {
        height: 150px;
        margin-bottom: 20px;
    }
}
</style><script>// --- Elementos del DOM ---
const passwordScreen = document.getElementById('passwordScreen');
const passwordInput = document.getElementById('passwordInput');
const passwordButton = document.getElementById('passwordButton');
const passwordError = document.getElementById('passwordError');
const passwordImageContainer = document.getElementById('passwordImageContainer');
const passwordDotsContainer = document.querySelector('.password-dots');
const passwordDots = document.querySelectorAll('.dot');

const hamburgerMenuBtn = document.getElementById('hamburgerMenuBtn');
const hamburgerMenu = document.getElementById('hamburgerMenu');
const getHintBtn = document.getElementById('getHint');
const creativeThinkingBtn = document.getElementById('creativeThinking');
const riddleTypesBtn = document.getElementById('riddleTypes');
const strongHintBtn = document.getElementById('strongHint');
const showAnswerBtn = document.getElementById('showAnswer');
const contactDadBtn = document.getElementById('contactDad');

const gameContainer = document.getElementById('gameContainer');
const titleElement = document.getElementById('title');
const descriptionElement = document.getElementById('description');
const riddleDisplay = document.getElementById('riddleDisplay');
const riddleTextElement = document.getElementById('riddleText');
const riddleInput = document.getElementById('riddleInput');
const submitRiddleButton = document.getElementById('submitRiddle');
const riddleFeedback = document.getElementById('riddleFeedback');
const finalMessageDiv = document.getElementById('finalMessage');
const restartButton = document.getElementById('restartButton');
const heartRainContainer = document.getElementById('heartRainContainer');
const riddleForElement = document.getElementById('riddleFor');
const fireworksContainer = document.getElementById('fireworksContainer');

// --- Configuración ---
const CORRECT_PASSWORD = "amor"; // <--- ¡ESTABLECE TU CONTRASEÑA SECRETA AQUÍ!
const DAD_WHATSAPP_NUMBER = "527471060076"; // <--- ¡TU NÚMERO DE TELÉFONO AQUÍ!
const WHATSAPP_MESSAGE_PASSWORD = "¡Papá! No podemos con la clave de amor... ¿Nos das una pista, por favor?";
const WHATSAPP_MESSAGE_RIDDLE = "¡Papá! Este acertijo es muy difícil... ¿Nos puedes ayudar?";

let typedPassword = "";
let score = 0; // Para llevar un conteo de respuestas correctas (se usa para penalizar ayuda)
let showAnswerUsed = false; // Controla si "Mostrar Respuesta" ya se usó

// Acertijos separados para cada una (60 para Mía y 60 para Sandra)
const riddlesMia = [
    { question: "¿Qué tiene un cuello pero no cabeza, y a veces lleva un vestido bonito?", answer: "botella", hint: "La usas para beber.", strongHint: "Es de vidrio o plástico y contiene líquidos." },
    { question: "Tengo hojas pero no soy árbol, tengo letras pero no hablo, y en mis páginas hay magia. ¿Qué soy?", answer: "libro", hint: "Me lees antes de dormir.", strongHint: "Lo abres para leer historias." },
    { question: "Vuelo sin alas, a veces soy de muchos colores, y aparezco después de la lluvia. ¿Qué soy?", answer: "arcoiris", hint: "Soy un puente de color en el cielo.", strongHint: "Tiene 7 colores y es un fenómeno natural." },
    { question: "Tengo corona pero no soy rey, soy muy dulce y me encanta estar en pasteles. ¿Qué soy?", answer: "fresa", hint: "Soy una fruta pequeña y roja.", strongHint: "Soy la fruta favorita de los postres y smoothies." },
    { question: "Soy una casita sin ventanas ni puertas, donde vive una gusanita que un día vuela. ¿Qué soy?", answer: "capullo", hint: "Donde las mariposas nacen.", strongHint: "Es la envoltura protectora de las larvas de algunos insectos." },
    { question: "Soy redondita y puedo botar, me encanta jugar y me puedes patear. ¿Qué soy?", answer: "pelota", hint: "La usas en el fútbol o baloncesto.", strongHint: "Es esférica y se usa para muchos deportes." },
    { question: "Tengo dientes pero no muerdo, me usas para pintar y hacer dibujos de mundos nuevos. ¿Qué soy?", answer: "lapiz", hint: "Lo usas para escribir en el cuaderno.", strongHint: "Está hecho de grafito y madera, y lo usas en la escuela." },
    { question: "Me puedes ver en el cielo, a veces de día y a veces de noche. Cambia mi forma, pero siempre estoy ahí. ¿Qué soy?", answer: "nube", hint: "Soy de algodón y a veces lloro (lluvia).", strongHint: "Está hecha de vapor de agua y flota en el cielo." },
    { question: "Tengo un ojo, pero no puedo ver; me usan para coser y unir pedacitos de tela. ¿Qué soy?", answer: "aguja", hint: "Famosa por su ojo, pero no ve.", strongHint: "Es delgada, puntiaguda y tiene un agujero para el hilo." },
    { question: "Siempre estoy delante de ti, pero no me puedes alcanzar; cada día soy nuevo, y no tengo fin. ¿Qué soy?", answer: "mañana", hint: "Viene después de la noche.", strongHint: "Es el día que sigue a hoy." },
    { question: "Soy blandito y dulce, me como con helado o en un pastel, y me encantan los conejos. ¿Qué soy?", answer: "zanahoria", hint: "Soy naranja y los conejos me adoran.", strongHint: "Es una raíz comestible, anaranjada y crujiente." },
    { question: "Tengo una cola pero no soy perro, puedo nadar y vivir en el mar. ¿Qué soy?", answer: "pez", hint: "Nado en el agua y tengo aletas.", strongHint: "Vive en el agua y respira por branquias." },
    { question: "Me pongo en tus pies para salir a pasear, y me desato si no me sabes atar. ¿Qué soy?", answer: "zapato", hint: "Me atas los cordones.", strongHint: "Lo usas para proteger tus pies y tiene suelas." },
    { question: "Tengo patas pero no camino, tengo respaldo pero no soy silla. En mí guardas tus secretos más preciados. ¿Qué soy?", answer: "cama", hint: "Donde duermes por las noches.", strongHint: "Mueble donde te acuestas para descansar." },
    { question: "Cuanto más caliente estoy, más me encojo. ¿Qué soy?", answer: "cera", hint: "Lo que gotea de una vela encendida.", strongHint: "Material con el que se hacen las velas." },
    { question: "Me inflan para jugar, y puedo volar alto con el viento. ¿Qué soy?", answer: "globo", hint: "Floto en las fiestas.", strongHint: "Se llena de aire o gas y puede flotar." },
    { question: "Tengo un tallo, pétalos de colores, y huelo muy bonito. Me regalas cuando quieres decir 'te quiero'. ¿Qué soy?", answer: "flor", hint: "La rosa es un ejemplo de mí.", strongHint: "Parte de una planta con pétalos y aroma." },
    { question: "Tengo alas, pero no soy pájaro; mi cuerpo es brillante, y me gusta la noche. ¿Qué soy?", answer: "luciernaga", hint: "Brillo en la oscuridad como una pequeña luz.", strongHint: "Insecto que emite luz en la oscuridad." },
    { question: "No tengo voz, pero cuento historias. No tengo manos, pero puedo dibujar sonrisas. ¿Qué soy?", answer: "imaginacion", hint: "Te permite soñar despierto.", strongHint: "La capacidad de crear ideas en tu mente." },
    { question: "Aunque me digas, no me dices; aunque me tomes, no me llevas. Soy lo que te falta cuando estás sola. ¿Qué soy?", answer: "compania", hint: "Estar con alguien.", strongHint: "Estar acompañado, no estar solo." },
    { question: "Vengo con el viento, pero no soy una hoja; tengo hilos, pero no soy una araña. ¿Qué soy?", answer: "cometa", hint: "Me elevas con una cuerda en el cielo.", strongHint: "Juguete que vuela con el viento y una cola." },
    { question: "Siempre me dan la vuelta, pero nunca me canso de dar vueltas. ¿Qué soy?", answer: "calcetin", hint: "Va en tu pie y lo volteas para guardarlo.", strongHint: "Prenda que cubre el pie y parte de la pierna." },
    { question: "Puedo ser larga o corta, me aprietas en el cuello para abrigarte. ¿Qué soy?", answer: "bufanda", hint: "Me usas en invierno para el frío.", strongHint: "Prenda de tela que se enrolla alrededor del cuello." },
    { question: "Tengo capa, pero no soy superhéroe; me ves en el jardín, pero no soy flor. Me usan para cocinar. ¿Qué soy?", answer: "cebolla", hint: "Me haces llorar cuando me cortas.", strongHint: "Hortaliza con varias capas y sabor fuerte." },
    { question: "Siempre estoy lleno de agujeros, pero aun así, retengo el agua. ¿Qué soy?", answer: "esponja", hint: "Me usas para bañarte o limpiar.", strongHint: "Material poroso que absorbe líquidos." },
    { question: "Soy alto cuando joven, y bajo cuando viejo. ¿Qué soy?", answer: "vela", hint: "Me enciendes para iluminar.", strongHint: "Cilindro de cera con una mecha que arde." },
    { question: "Tengo llaves, pero no cerraduras; tengo espacio, pero no habitación. En mí guardas tus pensamientos. ¿Qué soy?", answer: "teclado", hint: "Lo usas para escribir en la computadora.", strongHint: "Dispositivo de entrada con botones para introducir texto." },
    { question: "Me como sin pan, y se me puede echar sal o azúcar. ¿Qué soy?", answer: "huevo", hint: "Vengo de una gallina y me puedes cocinar.", strongHint: "Producto de aves, usado comúnmente en la cocina." },
    { question: "Soy un sonido que se escucha, pero no se ve; me gusta jugar al escondite en las montañas. ¿Qué soy?", answer: "eco", hint: "Soy la repetición de un sonido.", strongHint: "Fenómeno acústico de repetición de un sonido." },
    { question: "Tengo corazón pero no órganos, me gusta la tierra, y me usas para sembrar vida. ¿Qué soy?", answer: "semilla", hint: "Soy el inicio de una planta.", strongHint: "Parte del fruto que contiene el embrión de una planta." },
    { question: "Me llenan de aire, pero no soy un globo; me usas para flotar en el agua. ¿Qué soy?", answer: "flotador", hint: "Me usas en la piscina o en el mar para no hundirte.", strongHint: "Objeto inflable para mantenerse a flote." },
    { question: "Tengo un tronco, pero no soy un árbol; tengo brazos, pero no manos. Te doy un abrazo cálido. ¿Qué soy?", answer: "abrigo", hint: "Me pones encima cuando hace frío.", strongHint: "Prenda de vestir para proteger del frío." },
    { question: "Soy de cristal y me lleno de luz; me enciendo de noche y en la oscuridad. ¿Qué soy?", answer: "lampara", hint: "Me usas para iluminar tu cuarto.", strongHint: "Aparato que produce luz." },
    { question: "Me puedes romper con una palabra, pero si me tocas, no me sientes. ¿Qué soy?", answer: "silencio", hint: "Es la ausencia de ruido.", strongHint: "Falta de ruido o sonido." },
    { question: "Soy un puente sin río, un camino sin fin, y me recorro cada noche. ¿Qué soy?", answer: "sueño", hint: "Lo que haces cuando duermes.", strongHint: "Representación mental de imágenes y eventos mientras duermes." },
    { question: "Tengo agujas pero no coso, tengo números pero no cuento. ¿Qué soy?", answer: "reloj", hint: "Te digo la hora.", strongHint: "Instrumento para medir el tiempo." },
    { question: "Me ves en el cielo de día, soy grande y brillante, y me escondo de noche. ¿Qué soy?", answer: "sol", hint: "Me da calor y luz.", strongHint: "Estrella central de nuestro sistema planetario." },
    { question: "Tengo una cola, pero no soy animal; me gusta volar y soy de papel. ¿Qué soy?", answer: "papalote", hint: "Lo elevas en el parque con el viento.", strongHint: "Juguete de papel o tela que se eleva con una cuerda." },
    { question: "Visto de verde en verano y de colores en otoño. Me caigo en invierno y vuelvo en primavera. ¿Qué soy?", answer: "hoja", hint: "Soy parte de un árbol.", strongHint: "Órgano de las plantas, generalmente plano y verde." },
    { question: "Soy chiquito, pero puedo cruzar el mar. ¿Qué soy?", answer: "mensaje", hint: "Lo envías por teléfono o carta.", strongHint: "Comunicación que se envía de una persona a otra." },
    { question: "Me lleno de aire, pero no respiro; me pongo en tu casa, pero no soy puerta. ¿Qué soy?", answer: "colchon", hint: "Me usas para dormir en la cama.", strongHint: "Pieza acolchada sobre la que se duerme." },
    { question: "Tengo corazón y no tengo cuerpo. ¿Qué soy?", answer: "alcachofa", hint: "Es una verdura con forma de flor.", strongHint: "Hortaliza con un corazón tierno y comestible." },
    { question: "Soy de vidrio, pero no puedo ver; tengo boca, pero no hablo. Me usas para beber. ¿Qué soy?", answer: "vaso", hint: "Lo llenas de agua o jugo.", strongHint: "Recipiente para beber líquidos." },
    { question: "Tengo patas, pero no camino; tengo respaldo, pero no soy silla. Me usas para guardar cosas. ¿Qué soy?", answer: "mesa", hint: "Comes sobre ella.", strongHint: "Mueble con una superficie plana y patas." },
    { question: "Aunque me lancen, no me rompo; aunque me caiga, no me hago daño. Soy un juguete redondo. ¿Qué soy?", answer: "balon", hint: "Lo pateas en el campo.", strongHint: "Pelota grande usada en deportes." },
    { question: "Tengo espinas, pero no soy rosa; tengo agua, pero no soy río. Vivo en el desierto. ¿Qué soy?", answer: "cactus", hint: "Es una planta que vive en lugares secos.", strongHint: "Planta suculenta con tallos espinosos." },
    { question: "Soy de muchos colores, me pones en el techo para adornar, y me exploto con un '¡pop!'. ¿Qué soy?", answer: "confeti", hint: "Pequeños trozos de papel que se lanzan en fiestas.", strongHint: "Pedacitos de papel de colores que se usan en celebraciones." },
    { question: "Me usas para escribir, pero no tengo voz; tengo tinta, pero no sangro. ¿Qué soy?", answer: "pluma", hint: "Sustituye al lápiz para escribir con tinta.", strongHint: "Instrumento para escribir que usa tinta." },
    { question: "Aunque me tires, no me arrojas; aunque me recojas, no me llevas. Soy una prenda de vestir. ¿Qué soy?", answer: "camisa", hint: "Me pones en la parte de arriba del cuerpo.", strongHint: "Prenda de vestir que cubre el tronco y los brazos." },
    { question: "Tengo una cola, pero no soy un animal; me usas para volar sin moverte. ¿Qué soy?", answer: "avion", hint: "Vuelo por el cielo y llevo gente.", strongHint: "Vehículo que se desplaza por el aire." },
    { question: "Soy un sonido que no se puede tocar, pero te hace bailar. ¿Qué soy?", answer: "musica", hint: "La escuchas en la radio.", strongHint: "Combinación de sonidos y silencio que crea una melodía." },
    { question: "Tengo teclas, pero no cerraduras; tengo pantalla, pero no ventana. Me usas para jugar. ¿Qué soy?", answer: "consola", hint: "Donde juegas videojuegos.", strongHint: "Aparato electrónico para jugar videojuegos." },
    { question: "Soy un lugar donde hay muchos libros, y puedes aprender mucho. ¿Qué soy?", answer: "biblioteca", hint: "Donde pides prestados libros.", strongHint: "Edificio o sala donde se guardan libros." },
    { question: "Tengo una cabeza y un pie, pero no cuerpo. ¿Qué soy?", answer: "clavo", hint: "Lo golpeas con un martillo.", strongHint: "Pieza de metal puntiaguda para unir cosas." },
    { question: "Siempre estoy delante de ti, pero no me puedes ver. ¿Qué soy?", answer: "futuro", hint: "Lo que viene después.", strongHint: "Tiempo que está por venir." },
    { question: "Me abres cuando estás cansada, me cierras cuando descansas. ¿Qué soy?", answer: "ojos", hint: "Conmigo ves el mundo.", strongHint: "Órganos de la vista." },
    { question: "Soy alto o bajo, dulce o amargo, y se me come sin morder. ¿Qué soy?", answer: "gelatina", hint: "Es un postre que tiembla.", strongHint: "Alimento semisólido, a base de colágeno." },
    { question: "Tengo patas, pero no corro; tengo boca, pero no hablo. Me usas para tomar agua. ¿Qué soy?", answer: "grifo", hint: "De él sale el agua en el lavabo.", strongHint: "Dispositivo para controlar el flujo de agua." },
    { question: "Soy un cuento que no tiene fin, una aventura que siempre está por venir. ¿Qué soy?", answer: "imaginacion", hint: "Creas mundos en tu mente.", strongHint: "Capacidad de la mente de crear ideas nuevas." },
    { question: "Me das cuando tienes frío, me quitas cuando hace calor. ¿Qué soy?", answer: "bufanda", hint: "La usas en el cuello en invierno.", strongHint: "Prenda de abrigo para el cuello." },
    { question: "Tengo corazón, pero no late; tengo mesa, pero no se sienta. ¿Qué soy?", answer: "patata", hint: "Soy un tubérculo y me puedes freír.", strongHint: "Hortaliza subterránea, base de muchas comidas." }
];

const riddlesSandra = [
    { question: "Soy un sentimiento que no se ve, pero se siente con todo el ser, y tú me das cada día. ¿Qué soy?", answer: "cariño", hint: "Es el afecto o el aprecio por alguien.", strongHint: "Sentimiento de afecto y ternura hacia una persona." },
    { question: "Siempre estoy en tu mirada cuando me ves, y en tu sonrisa cuando eres feliz. Soy tu reflejo más bonito. ¿Qué soy?", answer: "alegria", hint: "Lo sientes cuando estás contento.", strongHint: "Sentimiento de satisfacción y bienestar." },
    { question: "Soy el lazo que nos une sin cuerdas, la melodía de nuestra vida. Me siento en cada abrazo. ¿Qué soy?", answer: "union", hint: "Es lo que hace que estemos juntos.", strongHint: "La acción de juntar o unir dos o más cosas." },
    { question: "Aunque me den, no me pierdo; aunque me rompan, no me voy. Soy el puente entre dos almas que se quieren. ¿Qué soy?", answer: "confianza", hint: "Creer en alguien sin dudar.", strongHint: "Seguridad que se tiene en algo o alguien." },
    { question: "Es lo más valioso que tengo, no se compra con dinero, y cada día contigo, vale un tesoro entero. ¿Qué es?", answer: "tiempo", hint: "Lo que pasa cada segundo.", strongHint: "La magnitud física que permite ordenar sucesos." },
    { question: "Soy un susurro suave en el viento, el calor en un abrazo, el latido de un sentimiento. ¿Qué soy?", answer: "ternura", hint: "Se siente al dar un abrazo suave.", strongHint: "Sentimiento de afecto, cariño o suavidad." },
    { question: "Cuando estoy presente, los miedos se van y el futuro se ilumina. Soy el poder de saber que todo saldrá bien. ¿Qué soy?", answer: "esperanza", hint: "El deseo de que algo bueno suceda.", strongHint: "Sentimiento de que se puede conseguir lo que se desea." },
    { question: "Soy el hilo invisible que conecta corazones, la fuerza que une generaciones. ¿Qué soy?", answer: "familia", hint: "Tu mamá, papá, hermanos...", strongHint: "Conjunto de personas unidas por parentesco." },
    { question: "Soy el eco de las risas, el reflejo de los abrazos, y la melodía que siempre suena en el corazón. ¿Qué soy?", answer: "recuerdo", hint: "Algo que pasó y está en tu memoria.", strongHint: "Imágen de un suceso pasado que se tiene en la memoria." },
    { question: "Lo más valioso que te puedo dar no tiene precio, se comparte en silencio, y crece con cada gesto. ¿Qué es?", answer: "presencia", hint: "Estar ahí para alguien.", strongHint: "Estar en un lugar o momento determinado." },
    { question: "Me das sin pedir, y recibo sin buscar. Soy el pilar que sostiene nuestro hogar. ¿Qué soy?", answer: "apoyo", hint: "Ayudar a alguien cuando lo necesita.", strongHint: "Ayuda o favor que se presta a alguien." },
    { question: "Soy el idioma universal que no necesita palabras, la fuerza que nos une, hoy y siempre. ¿Qué soy?", answer: "amor", hint: "El sentimiento más grande.", strongHint: "Sentimiento de afecto, pasión y entrega hacia algo o alguien." },
    { question: "Aunque la distancia nos separe, mi luz siempre te acompaña, como un faro en la oscuridad. ¿Qué soy?", answer: "esperanza", hint: "La fe en que algo bueno pasará.", strongHint: "Confianza en que ocurrirá algo que se desea." },
    { question: "Es un regalo que se renueva cada día, una promesa silenciosa de amor que nos guía. ¿Qué es?", answer: "vida", hint: "Lo que tienes cada día al despertar.", strongHint: "Existencia de los seres." },
    { question: "Siempre está delante, pero nunca llega. ¿Qué es?", answer: "futuro", hint: "Lo que aún no ha pasado.", strongHint: "El tiempo que está por venir." },
    { question: "Me inflan para jugar, y puedo volar alto con el viento. ¿Qué soy?", answer: "globo", hint: "Un juguete que flota en el aire.", strongHint: "Objeto de goma que se infla y vuela." },
    { question: "Tengo un tallo, pétalos de colores, y huelo muy bonito. Me regalas cuando quieres decir 'te quiero'. ¿Qué soy?", answer: "flor", hint: "La encuentras en un jardín.", strongHint: "Parte de una planta, a menudo con pétalos." },
    { question: "Tengo alas, pero no soy pájaro; mi cuerpo es brillante, y me gusta la noche. ¿Qué soy?", answer: "luciernaga", hint: "Un insecto que se ilumina.", strongHint: "Insecto que brilla en la oscuridad." },
    { question: "No tengo voz, pero cuento historias. No tengo manos, pero puedo dibujar sonrisas. ¿Qué soy?", answer: "imaginacion", hint: "Crear mundos en tu mente.", strongHint: "La facultad de la mente de crear ideas o imágenes." },
    { question: "Aunque me digas, no me dices; aunque me tomes, no me llevas. Soy lo que te falta cuando estás sola. ¿Qué soy?", answer: "compania", hint: "Estar acompañado.", strongHint: "Presencia de una o varias personas." },
    { question: "Aunque tenga muchos, no soy rico; pero soy muy dulce. ¿Qué soy?", answer: "beso", hint: "Lo das con los labios.", strongHint: "Contacto de los labios en señal de afecto." },
    { question: "Lo sientes cuando estás cerca, te da calor y te hace sentir feliz. ¿Qué es?", answer: "abrazo", hint: "Lo das con los brazos.", strongHint: "Acción de rodear con los brazos a alguien." },
    { question: "Soy un sonido que alegra el corazón, la banda sonora de la vida. ¿Qué soy?", answer: "risa", hint: "Lo haces cuando algo es gracioso.", strongHint: "Sonido producido al reír." },
    { question: "Soy un lugar sin paredes ni techo, donde los secretos del corazón se guardan. ¿Qué soy?", answer: "corazon", hint: "Bombea sangre y es símbolo de amor.", strongHint: "Órgano que bombea la sangre y representa los sentimientos." },
    { question: "Soy un hilo invisible que conecta almas, la fuerza que nunca se rompe. ¿Qué soy?", answer: "amistad", hint: "El cariño entre amigos.", strongHint: "Afecto personal puro y desinteresado." },
    { question: "Me das sin esperar nada a cambio, y soy la mayor riqueza. ¿Qué soy?", answer: "felicidad", hint: "Lo que sientes cuando estás muy contento.", strongHint: "Estado de ánimo de la persona que se siente plenamente satisfecha." },
    { question: "Soy el reflejo de lo que sientes por dentro, y brillas con luz propia. ¿Qué soy?", answer: "sonrisa", hint: "La pones en tu cara cuando estás alegre.", strongHint: "Expresión facial de alegría o placer." },
    { question: "Aunque me busques, no me encuentras; pero estoy en cada momento de alegría. ¿Qué soy?", answer: "paz", hint: "Ausencia de conflicto o intranquilidad.", strongHint: "Estado de tranquilidad y sosiego." },
    { question: "Soy la luz que disipa la oscuridad, la guía en el camino. ¿Qué soy?", answer: "sabiduria", hint: "Conocimiento profundo de las cosas.", strongHint: "Conocimiento que se adquiere a través de la experiencia y el estudio." },
    { question: "Soy un jardín lleno de emociones, y florezco con cada risa. ¿Qué soy?", answer: "alma", hint: "Es tu parte espiritual.", strongHint: "Parte inmaterial del ser humano." },
    { question: "Me renuevo cada día, me despierto con el sol, y te doy una nueva oportunidad. ¿Qué soy?", answer: "dia", hint: "Viene después de la noche.", strongHint: "Periodo de 24 horas." },
    { question: "Tengo muchas palabras, pero no hablo; te enseño y te hago crecer. ¿Qué soy?", answer: "conocimiento", hint: "Lo que aprendes en la escuela.", strongHint: "Conjunto de saberes sobre un tema o ciencia." },
    { question: "Soy un tesoro que no tiene precio, y se comparte entre dos corazones. ¿Qué soy?", answer: "secreto", hint: "Algo que no se cuenta a todos.", strongHint: "Cosa que se mantiene oculta." },
    { question: "Me das cuando me escuchas, y te doy cuando hablo. ¿Qué soy?", answer: "atencion", hint: "Poner tus cinco sentidos en algo.", strongHint: "Acto de escuchar o mirar con interés." },
    { question: "Soy la melodía de tu existencia, la historia de cada paso. ¿Qué soy?", answer: "vida", hint: "Lo que tienes desde que naces.", strongHint: "Conjunto de propiedades de los seres vivos." },
    { question: "Me ves en los ojos de quien te quiere, y brillas con luz propia. ¿Qué soy?", answer: "brillo", hint: "Luz intensa y clara.", strongHint: "Luz que emite o refleja un cuerpo." },
    { question: "Soy el comienzo de todo, la chispa que enciende los sueños. ¿Qué soy?", answer: "idea", hint: "Un pensamiento en tu mente.", strongHint: "Representación mental de algo." },
    { question: "Me das con cada gesto, me recibes con cada palabra. Soy el puente del entendimiento. ¿Qué soy?", answer: "comprension", hint: "Entender algo o a alguien.", strongHint: "Capacidad de entender o percibir las cosas." },
    { question: "Soy un regalo que no se envuelve, una alegría que se comparte. ¿Qué soy?", answer: "paz", hint: "Tranquilidad y calma.", strongHint: "Estado de no perturbación." },
    { question: "Siempre estoy contigo, aunque no me veas; te doy fuerza y consuelo. ¿Qué soy?", answer: "energia", hint: "La fuerza para moverte.", strongHint: "Capacidad para realizar un trabajo." },
    { question: "Soy el reflejo de tu ser, lo más auténtico que posees. ¿Qué soy?", answer: "personalidad", hint: "Lo que te hace único.", strongHint: "Conjunto de características que definen a una persona." },
    { question: "Me das cuando me perdonas, y me recibes cuando te arrepientes. ¿Qué soy?", answer: "compasion", hint: "Sentir pena por el sufrimiento de otro.", strongHint: "Sentimiento de tristeza ante el sufrimiento ajeno." },
    { question: "Soy un eco en el tiempo, una huella que no se borra. ¿Qué soy?", answer: "legado", hint: "Lo que dejas para el futuro.", strongHint: "Herencia o transmisión de bienes o conocimientos." },
    { question: "Me das cuando confías, me recibes cuando demuestras. ¿Qué soy?", answer: "lealtad", hint: "Fidelidad y compromiso.", strongHint: "Sentimiento de devoción y fidelidad." },
    { question: "Soy la base de todo, el inicio de una aventura. ¿Qué soy?", answer: "creacion", hint: "Dar origen a algo nuevo.", strongHint: "Acción de crear o establecer algo." },
    { question: "Me das con cada paso, y soy el camino que te lleva. ¿Qué soy?", answer: "destino", hint: "El futuro que ya está escrito.", strongHint: "Serie de acontecimientos que le suceden a una persona." },
    { question: "Soy un lenguaje sin palabras, una conexión sin fin. ¿Qué soy?", answer: "empatia", hint: "Ponerte en el lugar de otro.", strongHint: "Capacidad de comprender y compartir los sentimientos de otro." },
    { question: "Me das con cada momento, y soy el recuerdo que atesoras. ¿Qué soy?", answer: "experiencia", hint: "Lo que aprendes viviendo.", strongHint: "Conocimiento adquirido a través de la práctica." },
    { question: "Soy un susurro en el alma, una guía en la oscuridad. ¿Qué soy?", answer: "intuicion", hint: "Saber algo sin saber cómo.", strongHint: "Capacidad de comprender las cosas de forma instantánea." },
    { question: "Me das cuando perdonas, me recibes cuando te reconcilias. ¿Qué soy?", answer: "perdon", hint: "Olvidar una ofensa.", strongHint: "Acción de perdonar una ofensa o deuda." },
    { question: "Soy el motor que impulsa, la fuerza que te mueve. ¿Qué soy?", answer: "motivacion", hint: "Razón para actuar.", strongHint: "Conjunto de factores que impulsan a una persona a actuar." },
    { question: "Me das con cada gesto, y soy el bienestar que te ofrezco. ¿Qué soy?", answer: "cuidado", hint: "Atención y protección.", strongHint: "Acción de cuidar o proteger algo o a alguien." },
    { question: "Soy la luz que brilla en tu interior, y te hace única. ¿Qué soy?", answer: "esencia", hint: "Lo más importante de algo.", strongHint: "Naturaleza de una cosa o persona." },
    { question: "Me das con cada palabra, y soy el lazo que nos une. ¿Qué soy?", answer: "dialogo", hint: "Conversar entre dos o más personas.", strongHint: "Conversación entre dos o más personas." },
    { question: "Soy el principio de la sabiduría, el inicio del crecimiento. ¿Qué soy?", answer: "curiosidad", hint: "Deseo de saber o aprender.", strongHint: "Interés por conocer o descubrir cosas nuevas." },
    { question: "Me das cuando me compartes, y crezco con cada vida. ¿Qué soy?", answer: "conocimiento", hint: "Lo que sabes y aprendes.", strongHint: "Conjunto de saberes que se tienen sobre algo." },
    { question: "Soy la música del corazón, la danza de las emociones. ¿Qué soy?", answer: "armonia", hint: "Equilibrio y buena relación.", strongHint: "Concordancia de voces o sonidos." },
    { question: "Me das con cada paso, y soy la senda que construyes. ¿Qué soy?", answer: "camino", hint: "Ruta o dirección.", strongHint: "Vía por donde se transita." },
    { question: "Soy la flor que nunca se marchita, el amor que siempre florece. ¿Qué soy?", answer: "eternidad", hint: "Tiempo sin fin.", strongHint: "Duración que no tiene fin." },
    { question: "Me das con cada sonrisa, y soy la luz que ilumina tu día. ¿Qué soy?", answer: "alegria", hint: "Sentimiento de felicidad.", strongHint: "Estado de ánimo que se manifiesta con la risa." }
];

let currentMiaRiddleIndex = 0;
let currentSandraRiddleIndex = 0;
let turn = 'Mia';

// --- Funciones del Juego ---

/**
 * Carga el siguiente acertijo en la interfaz, alternando entre Mía y Sandra.
 * Si todos los acertijos han sido resueltos, muestra el mensaje final.
 */
function loadRiddle() {
    let currentRiddle;
    let targetName;

    if (turn === 'Mia') {
        if (currentMiaRiddleIndex < riddlesMia.length) {
            currentRiddle = riddlesMia[currentMiaRiddleIndex];
            targetName = "Mía Guadalupe";
        } else {
            // Si Mía terminó, cambiamos a Sandra
            turn = 'Sandra';
            if (currentSandraRiddleIndex >= riddlesSandra.length) {
                // Si Sandra también terminó, mostramos el mensaje final
                showFinalMessage();
                return;
            }
            // Si Sandra aún tiene acertijos, cargamos el de ella
            loadRiddle();
            return;
        }
    } else { // turn === 'Sandra'
        if (currentSandraRiddleIndex < riddlesSandra.length) {
            currentRiddle = riddlesSandra[currentSandraRiddleIndex];
            targetName = "Sandra";
        } else {
            // Si Sandra terminó, cambiamos a Mía (por si acaso quedaron acertijos pendientes de Mía, aunque el flujo es secuencial)
            turn = 'Mia';
            if (currentMiaRiddleIndex >= riddlesMia.length) {
                // Si Mía también terminó, mostramos el mensaje final
                showFinalMessage();
                return;
            }
            // Si Mía aún tiene acertijos, cargamos el de ella
            loadRiddle();
            return;
        }
    }

    riddleForElement.textContent = targetName;
    riddleTextElement.textContent = currentRiddle.question;
    riddleInput.value = '';
    riddleFeedback.textContent = '';
    submitRiddleButton.disabled = false;
    riddleInput.focus();
}

/**
 * Verifica la respuesta del acertijo actual.
 * Proporciona feedback y avanza al siguiente acertijo si es correcto.
 */
function checkRiddle() {
    const userAnswer = riddleInput.value.trim().toLowerCase();
    let currentRiddle;

    if (turn === 'Mia') {
        currentRiddle = riddlesMia[currentMiaRiddleIndex];
    } else {
        currentRiddle = riddlesSandra[currentSandraRiddleIndex];
    }

    if (!currentRiddle) {
        console.error("No hay acertijo disponible para verificar.");
        return;
    }

    const correctAnswer = currentRiddle.answer.toLowerCase();

    if (userAnswer === correctAnswer) {
        riddleFeedback.textContent = '¡Súper bien! ¡Un corazón más cerca! ✅';
        riddleFeedback.style.color = '#4CAF50';
        submitRiddleButton.disabled = true;
        score++;

        // Activar la opción "Mostrar Respuesta" después del primer acierto
        if (score === 1) { // Podrías cambiar esto a si currentMiaRiddleIndex > 0 || currentSandraRiddleIndex > 0
            showAnswerBtn.classList.remove('disabled-option');
        }

        setTimeout(() => {
            if (turn === 'Mia') {
                currentMiaRiddleIndex++;
            } else {
                currentSandraRiddleIndex++;
            }
            turn = (turn === 'Mia') ? 'Sandra' : 'Mia'; // Alternar turno
            loadRiddle();
        }, 1500);
    } else {
        riddleFeedback.textContent = '¡Ah, ah! Piensen un poquito más... ¡Ustedes pueden! 🤔';
        riddleFeedback.style.color = '#FF4D94';
    }
}

/**
 * Muestra el mensaje final del juego y activa las animaciones de celebración.
 */
function showFinalMessage() {
    riddleDisplay.classList.add('hidden');
    finalMessageDiv.classList.remove('hidden');
    titleElement.textContent = '¡Lo lograron, mis ingeniosas princesas! 🎉';
    descriptionElement.classList.add('hidden');
    stopHeartRain();
    launchFireworks();
}

/**
 * Reinicia el juego a su estado inicial, volviendo a la pantalla de contraseña.
 */
function restartGame() {
    currentMiaRiddleIndex = 0;
    currentSandraRiddleIndex = 0;
    turn = 'Mia';
    score = 0;
    showAnswerUsed = false; // Reiniciar el contador de uso de "Mostrar Respuesta"

    finalMessageDiv.classList.add('hidden');
    riddleDisplay.classList.remove('hidden');
    titleElement.innerHTML = 'Vamos a jugar muñecas <span class="heart">💖</span>';
    descriptionElement.classList.remove('hidden');
    riddleInput.value = '';
    fireworksContainer.innerHTML = '';

    passwordScreen.style.display = 'flex';
    passwordScreen.style.opacity = 1;
    gameContainer.classList.remove('visible');
    passwordInput.value = '';
    typedPassword = "";
    updatePasswordDots();
    passwordError.classList.add('hidden');
    passwordInput.focus();
    startHeartRain();
    startMagicParticles();

    // Deshabilitar la opción "Mostrar Respuesta" al reiniciar
    showAnswerBtn.classList.add('disabled-option');
}

// --- Lógica de la Pantalla de Contraseña Interactiva ---

/**
 * Actualiza el estado visual de los puntos de la contraseña según lo tecleado.
 */
function updatePasswordDots() {
    passwordDots.forEach((dot, index) => {
        if (index < typedPassword.length) {
            dot.classList.add('filled');
        } else {
            dot.classList.remove('filled');
            dot.classList.remove('incorrect');
        }
    });
}

/**
 * Verifica la contraseña ingresada. Si es correcta, transiciona a la pantalla del juego.
 */
function checkPassword() {
    if (typedPassword.toLowerCase() === CORRECT_PASSWORD) {
        passwordScreen.style.opacity = 0;
        passwordScreen.addEventListener('transitionend', () => {
            passwordScreen.style.display = 'none';
            gameContainer.classList.add('visible');
            loadRiddle();
        }, { once: true });
    } else {
        passwordError.classList.remove('hidden');
        passwordDots.forEach(dot => dot.classList.add('incorrect'));
        setTimeout(() => {
            typedPassword = "";
            updatePasswordDots();
            passwordError.classList.add('hidden');
            passwordInput.focus();
        }, 800);
    }
}

// --- Lógica del Menú de Hamburguesa ---
function toggleHamburgerMenu() {
    hamburgerMenu.classList.toggle('hidden');
    hamburgerMenu.classList.toggle('open');
    hamburgerMenuBtn.classList.toggle('open');
}

/** Muestra consejos generales para resolver acertijos. */
function showCreativeThinkingTips() {
    alert(
        "**Desbloqueen su Pensamiento Creativo:**\n\n" +
        "1.  **No hay respuestas 'tontas':** Anoten todas las ideas que se les ocurran, por más locas que parezcan. ¡A veces la más loca es la correcta!\n" +
        "2.  **Jueguen con las palabras:** ¿Hay rimas? ¿Juegos de palabras? ¿Doble sentido?\n" +
        "3.  **Cambien la perspectiva:** Imaginen que son el objeto del acertijo, ¿cómo se sentirían? ¿Qué harían?\n" +
        "4.  **Colaboren:** ¡Dos cabezas piensan mejor que una! Compartan sus ideas y escuchen las de la otra.\n" +
        "5.  **Tomen un respiro:** Si se sienten frustradas, pausen, tomen un vaso de agua, y vuelvan con la mente fresca."
    );
}

/** Muestra ejemplos de tipos comunes de acertijos. */
function showRiddleTypesTips() {
    alert(
        "**Tipos de Acertijos Comunes:**\n\n" +
        "1.  **Metáfora/Descripción:** Describen un objeto o concepto usando cualidades que no le pertenecen literalmente (ej. 'Tengo cuello pero no cabeza').\n" +
        "2.  **Juego de Palabras:** Usan doble sentido, homónimos o rimas para confundir y guiar a la vez.\n" +
        "3.  **Lógicos:** Requieren deducir la respuesta a partir de la información dada, eliminando posibilidades.\n" +
        "4.  **De Observación:** Se basan en detalles que pueden pasar desapercibidos a primera vista.\n" +
        "5.  **De Conocimiento General:** Pueden requerir un poco de conocimiento sobre algo específico, pero siempre con una pista ingeniosa."
    );
}

function handleHelpOption(option) {
    let message = "";
    let currentRiddle = null;
    let askingForPasswordHelp = passwordScreen.style.display !== 'none'; // ¿Están en la pantalla de contraseña?

    // Obtener el acertijo actual solo si NO están en la pantalla de contraseña
    if (!askingForPasswordHelp) {
        if (turn === 'Mia' && currentMiaRiddleIndex < riddlesMia.length) {
            currentRiddle = riddlesMia[currentMiaRiddleIndex];
        } else if (turn === 'Sandra' && currentSandraRiddleIndex < riddlesSandra.length) {
            currentRiddle = riddlesSandra[currentSandraRiddleIndex];
        }
    }

    switch (option) {
        case 'hint':
            if (currentRiddle && currentRiddle.hint) {
                message = `Pista para ${riddleForElement.textContent}: "${currentRiddle.hint}"`;
                score = Math.max(0, score - 1); // Penalización leve por usar pista
            } else {
                message = "¡Uhm! En este momento no hay un acertijo activo para dar una pista, o este no tiene una. ¡Sigan pensando con amor!";
            }
            break;
        case 'strongHint':
            if (currentRiddle && currentRiddle.strongHint) {
                message = `¡Uf! ¿Necesitan una súper pista? Aquí va para ${riddleForElement.textContent}: "${currentRiddle.strongHint}"`;
                score = Math.max(0, score - 3); // Penalización moderada por pista fuerte
            } else {
                message = "¡Ay! Este acertijo no tiene una súper pista extra. ¡Pero ustedes pueden!";
            }
            break;
        case 'showAnswer':
            if (showAnswerUsed) {
                message = "¡Uhm! La opción 'Mostrar Respuesta' ya fue utilizada. ¡A seguir pensando con su propio ingenio!";
            } else if (currentRiddle) {
                const confirmReveal = confirm(`¡Cuidado! ¿Están SEGURAS de que quieren ver la respuesta? Esto les quitará muchos puntos y la diversión del acertijo. La respuesta es para ${riddleForElement.textContent}.`);
                if (confirmReveal) {
                    message = `¡Oh, oh! ¡Haciendo trampa con amor! La respuesta era: **${currentRiddle.answer}**. ¡Pero el próximo lo resuelven ustedes solitas! 😉`;
                    score = Math.max(0, score - 5); // Penalización fuerte por mostrar respuesta
                    showAnswerUsed = true; // Marcar como usada
                    showAnswerBtn.classList.add('disabled-option'); // Deshabilitar la opción
                } else {
                    message = "¡Bien hecho! ¡Es mejor seguir intentando! 😉";
                }
            } else {
                message = "¡Jajaja! No hay acertijo activo para revelar una respuesta. ¡Pero ya sabemos que te gusta ir al grano! 😉";
            }
            break;
        case 'contactDad':
            let whatsappMessage = askingForPasswordHelp ? WHATSAPP_MESSAGE_PASSWORD : WHATSAPP_MESSAGE_RIDDLE;
            const whatsappLink = `https://wa.me/${DAD_WHATSAPP_NUMBER}?text=${encodeURIComponent(whatsappMessage)}`;
            window.open(whatsappLink, '_blank');
            message = "¡Mensaje a Papá enviado! Él estará feliz de ayudarles. 😉";
            break;
        case 'creative':
            showCreativeThinkingTips();
            break;
        case 'types':
            showRiddleTypesTips();
            break;
    }
    // Solo mostrar alert si hay un mensaje generado por la opción (y no es una de las "tips")
    if (option !== 'creative' && option !== 'types') {
        alert(message);
    }
    toggleHamburgerMenu(); // Cerrar menú después de seleccionar opción
}


// --- Manejadores de Eventos ---
passwordInput.addEventListener('input', (event) => {
    typedPassword = event.target.value;
    updatePasswordDots();
    passwordError.classList.add('hidden');

    if (typedPassword.length === CORRECT_PASSWORD.length) {
        checkPassword();
    }
});

passwordButton.addEventListener('click', checkPassword);

passwordInput.addEventListener('keypress', (event) => {
    if (event.key === 'Enter') {
        checkPassword();
    }
});

submitRiddleButton.addEventListener('click', checkRiddle);
riddleInput.addEventListener('keypress', (event) => {
    if (event.key === 'Enter') {
        checkRiddle();
    }
});

restartButton.addEventListener('click', restartGame);

// Eventos del menú de hamburguesa
hamburgerMenuBtn.addEventListener('click', toggleHamburgerMenu);
getHintBtn.addEventListener('click', () => handleHelpOption('hint'));
creativeThinkingBtn.addEventListener('click', () => handleHelpOption('creative'));
riddleTypesBtn.addEventListener('click', () => handleHelpOption('types'));
strongHintBtn.addEventListener('click', () => handleHelpOption('strongHint'));
showAnswerBtn.addEventListener('click', () => handleHelpOption('showAnswer'));
contactDadBtn.addEventListener('click', () => handleHelpOption('contactDad'));


// --- Funciones de Animación (sin cambios significativos) ---

let particleInterval;
/** Crea y añade una partícula de "polvo mágico" a la pantalla de contraseña. */
function createMagicParticle() {
    const particle = document.createElement('div');
    particle.classList.add('magic-particle');
    const size = Math.random() * 3 + 2; // 2 a 5px
    particle.style.width = `${size}px`;
    particle.style.height = `${size}px`;

    const x = Math.random() * 100; // 0 a 100% del ancho del contenedor
    const y = Math.random() * 100; // 0 a 100% de la altura del contenedor
    particle.style.left = `${x}%`;
    particle.style.top = `${y}%`;

    const startX = `${(Math.random() - 0.5) * 50}px`;
    const startY = `${(Math.random() - 0.5) * 50}px`;
    const endX = `${(Math.random() - 0.5) * 50}px`;
    const endY = `${(Math.random() - 0.5) * 50}px`;
    particle.style.setProperty('--startX', startX);
    particle.style.setProperty('--startY', startY);
    particle.style.setProperty('--endX', endX);
    particle.style.setProperty('--endY', endY);

    particle.style.animationDuration = `${Math.random() * 5 + 5}s`;
    particle.style.animationDelay = `${Math.random() * 2}s`;

    if (passwordImageContainer) {
        passwordImageContainer.appendChild(particle);
        particle.addEventListener('animationend', () => particle.remove());
    } else {
        particle.remove();
    }
}

/** Inicia la generación de partículas de polvo mágico. */
function startMagicParticles() {
    if (particleInterval) clearInterval(particleInterval);
    if (passwordScreen.style.display !== 'none') {
        particleInterval = setInterval(createMagicParticle, 150);
    }
}

/** Detiene la generación de partículas de polvo mágico y las elimina. */
function stopMagicParticles() {
    clearInterval(particleInterval);
    document.querySelectorAll('.magic-particle').forEach(p => p.remove());
}

let heartInterval;
/** Crea y añade un corazón que cae a la lluvia de corazones. */
function createHeart() {
    const heart = document.createElement('span');
    const hearts = ['❤️', '💖', '💗', '💞', '💜', '💙', '💛', '💚', '🧡'];
    heart.innerHTML = hearts[Math.floor(Math.random() * hearts.length)];
    heart.style.left = Math.random() * 100 + 'vw';
    heart.style.animationDuration = Math.random() * 2 + 3 + 's';
    heart.style.animationDelay = Math.random() * 0.5 + 's';
    const xEnd = (Math.random() - 0.5) * 50;
    heart.style.setProperty('--x-end', xEnd + 'vw');
    heart.style.transform = `rotate(${Math.random() * 360}deg)`;

    heartRainContainer.appendChild(heart);
    heart.addEventListener('animationend', () => {
        heart.remove();
    });
}

/** Inicia la lluvia de corazones. */
function startHeartRain() {
    if (heartInterval) clearInterval(heartInterval);
    heartInterval = setInterval(createHeart, 200);
}

/** Detiene la lluvia de corazones y elimina los corazones existentes. */
function stopHeartRain() {
    clearInterval(heartInterval);
    heartRainContainer.innerHTML = '';
}

/**
 * Crea un efecto de fuego artificial en una posición específica.
 * @param {number} x - Posición X en vh (viewport height).
 * @param {number} y - Posición Y en vw (viewport width).
 */
function createFirework(x, y) {
    const firework = document.createElement('div');
    firework.classList.add('firework');
    firework.style.left = `${x}vw`;
    firework.style.top = `${y}vh`;

    const colors = ['#FFC0CB', '#FFD700', '#B19CD9', '#FF69B4', '#FFFACD', '#98FB98'];
    const color = colors[Math.floor(Math.random() * colors.length)];
    firework.style.backgroundColor = color;
    firework.style.boxShadow = `0 0 15px ${color}`;

    const numParticles = Math.floor(Math.random() * 10) + 5;
    for (let i = 0; i < numParticles; i++) {
        const particle = document.createElement('div');
        particle.classList.add('firework-particle');
        particle.style.width = '5px';
        particle.style.height = '5px';
        particle.style.borderRadius = '50%';
        particle.style.backgroundColor = color;
        particle.style.position = 'absolute';
        particle.style.left = '0';
        particle.style.top = '0';
        particle.style.opacity = '0';
        particle.style.transform = 'scale(0)';

        const angle = Math.random() * Math.PI * 2;
        const distance = Math.random() * 50 + 20;
        const duration = Math.random() * 1 + 0.8;

        particle.style.animation = `
            explodeParticle ${duration}s forwards ease-out
        `;
        particle.style.setProperty('--endX', `${Math.cos(angle) * distance}px`);
        particle.style.setProperty('--endY', `${Math.sin(angle) * distance}px`);
        firework.appendChild(particle);

        particle.addEventListener('animationend', () => particle.remove());
    }

    fireworksContainer.appendChild(firework);
    firework.addEventListener('animationend', () => firework.remove());
}

/** Lanza múltiples fuegos artificiales en la pantalla. */
function launchFireworks() {
    for (let i = 0; i < 5; i++) {
        setTimeout(() => {
            for (let j = 0; j < 5; j++) {
                const x = Math.random() * 80 + 10;
                const y = Math.random() * 60 + 10;
                setTimeout(() => createFirework(x, y), Math.random() * 500);
            }
        }, i * 800);
    }
}

// --- Carga Inicial ---
window.onload = () => {
    startMagicParticles();
    startHeartRain();
    passwordInput.focus();
    // Deshabilitar la opción "Mostrar Respuesta" al cargar la página
    showAnswerBtn.classList.add('disabled-option');
};
</script>]
