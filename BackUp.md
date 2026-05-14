<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Boda - Joan & Alexia</title>

    <link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">

    <style>
        * { margin:0; padding:0; box-sizing:border-box; }

        body {
            font-family: 'Poppins', sans-serif;
            background: #fff8dc;
            color: #444;
            text-align: center;
            overflow-x: hidden;
        }

        /* OVERLAY - PANTALLA DE INICIO */
        .overlay {
            position: fixed;
            top: 0; left: 0;
            width: 100%;
            height: 100%;
            /* Usamos Boda1 como fondo de bienvenida */
            background: linear-gradient(rgba(255,248,220,0.85), rgba(255,248,220,0.85)),
                        url('Boda1.jpeg') center/cover no-repeat;
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 10000;
            transition: opacity 0.8s ease;
        }

        .overlay-content {
            text-align: center;
            animation: fadeIn 1.5s ease;
            backdrop-filter: blur(5px);
            padding: 30px;
        }

        .intro {
            font-size: 1.1rem;
            letter-spacing: 3px;
            text-transform: uppercase;
            color: #777;
            margin-bottom: 10px;
        }

        .names {
            font-family: 'Great Vibes', cursive;
            font-size: 5rem;
            color: #d4af37;
            margin: 15px 0;
        }

        .date {
            font-size: 1.4rem;
            font-weight: 300;
            margin-bottom: 20px;
        }

        .frase {
            font-style: italic;
            margin-bottom: 40px;
            color: #666;
            font-size: 1.1rem;
        }

        /* BOTÓN PREMIUM AESTHETIC */
        .btn-open {
            padding: 22px 75px;
            font-family: 'Poppins', sans-serif;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 2.5px;
            font-size: 1rem;
            color: #a67c00;
            background: linear-gradient(135deg, #fff3b0 0%, #ffe48a 50%, #ffd700 100%);
            border: 1px solid #ffd700;
            border-radius: 4px;
            cursor: pointer;
            position: relative;
            overflow: hidden;
            box-shadow: 0 10px 25px rgba(212,175,55,0.3);
            transition: all 0.4s ease;
        }

        .btn-open:hover {
            transform: scale(1.05);
            box-shadow: 0 15px 35px rgba(212,175,55,0.5);
            letter-spacing: 3.5px;
        }

        .btn-open::after {
            content: '';
            position: absolute;
            top: 0; left: -150%;
            width: 100%; height: 100%;
            background: linear-gradient(120deg, transparent, rgba(255,255,255,0.8), transparent);
            transform: skewX(-20deg);
            transition: 0.8s ease;
        }

        .btn-open:hover::after { left: 150%; }

        /* HEADER PRINCIPAL */
        header {
            height: 100vh;
            /* Usamos Boda2 como fondo principal */
            background: linear-gradient(rgba(0,0,0,0.3), rgba(0,0,0,0.3)),
                        url('Boda2.jpeg') center/cover no-repeat;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            color: white;
            text-shadow: 2px 2px 10px rgba(0,0,0,0.5);
        }

        header h1 { font-family:'Great Vibes', cursive; font-size: 5rem; }

        /* SECCIONES */
        section { padding: 80px 20px; max-width: 900px; margin: auto; }
        h2 { font-family: 'Great Vibes', cursive; font-size: 3rem; color: #d4af37; margin-bottom: 30px; }

        /* CONTADOR */
        .countdown {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 20px;
            flex-wrap: wrap;
        }

        .box {
            background: white;
            padding: 20px;
            min-width: 90px;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(212,175,55,0.15);
            border-bottom: 3px solid #d4af37;
        }

        .box span { font-size: 1.8rem; font-weight: 600; color: #444; }

        /* GALERÍA */
        .gallery {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
        }

        .gallery img {
            width: 100%;
            height: 350px;
            object-fit: cover;
            border-radius: 8px;
            cursor: pointer;
            transition: 0.4s;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
        }

        .gallery img:hover { transform: scale(1.03); box-shadow: 0 8px 20px rgba(0,0,0,0.2); }

        /* MODAL ZOOM */
        .modal {
            display: none;
            position: fixed;
            top: 0; left: 0;
            width: 100%; height: 100%;
            background: rgba(0,0,0,0.9);
            justify-content: center;
            align-items: center;
            z-index: 11000;
        }

        .modal img { max-width: 90%; max-height: 85%; border: 8px solid white; border-radius: 4px; }

        /* ANIMACIONES */
        .fade {
            opacity: 0;
            transform: translateY(30px);
            transition: 1s ease-out;
        }

        .show {
            opacity: 1;
            transform: translateY(0);
        }

        .music-btn {
            position: fixed;
            bottom: 30px;
            right: 30px;
            background: #d4af37;
            color: white;
            border: none;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            cursor: pointer;
            box-shadow: 0 4px 10px rgba(0,0,0,0.3);
            z-index: 999;
            font-size: 1.2rem;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
    </style>
</head>

<body>

<!-- OVERLAY INICIAL -->
<div class="overlay" id="overlay">
    <div class="overlay-content">
        <p class="intro">¡Nos casamos!</p>
        <h1 class="names">Joan & Alexia</h1>
        <p class="date">10 de Octubre 2026</p>
        <p class="frase">“Dos corazones, un mismo camino”</p>
        <button class="btn-open" onclick="entrar()"> Ver invitación </button>
    </div>
</div>

<header>
    <h1 class="fade">Joan & Alexia</h1>
    <p class="fade" style="font-size: 1.5rem; letter-spacing: 2px;">10.10.2026</p>
</header>

<section class="fade invitation-text">
    <p>
        Hay momentos en la vida que, por sí solos, ya son especiales.
        Pero cuando se comparten con las personas que más queremos,
        se vuelven verdaderamente inolvidables.
    </p>

    <p class="highlight">
        Por eso, con mucha alegría,
        queremos invitarte a ser parte de este día tan importante para nosotros:
        <strong>Nuestra boda</strong>.
    </p>
</section>

<section class="fade">
    <h2>Faltan</h2>
    <div class="countdown">
        <div class="box"><span id="dias">0</span><br>Días</div>
        <div class="box"><span id="horas">0</span><br>Hs</div>
        <div class="box"><span id="minutos">0</span><br>Min</div>
        <div class="box"><span id="segundos">0</span><br>Seg</div>
    </div>
</section>


<section class="bible-verse fade">
    <p class="verse">
        "El amor es paciente, es bondadoso. El amor no es envidioso ni jactancioso ni orgulloso.
        No hace nada indebido, no busca lo suyo, no se irrita, no guarda rencor.
        Todo lo disculpa, todo lo cree, todo lo espera, todo lo soporta."
    </p>
    <strong><span class="verse-ref">1 Corintios 13:4-7</span></strong>
</section>

<section class="fade">
    <h2>Nuestros Momentos</h2>
    <div class="gallery">
        <img src="Boda1.jpeg" onclick="zoom(this)" alt="Nuestra Boda 1">
        <img src="Boda2.jpeg" onclick="zoom(this)" alt="Nuestra Boda 2">
        <img src="Boda3.jpeg" onclick="zoom(this)" alt="Nuestra Boda 3">
        <img src="Boda4.jpeg" onclick="zoom(this)" alt="Nuestra Boda 4">
    </div>
</section>

<div class="modal" id="modal" onclick="cerrar()">
    <img id="imgZoom">
</div>

<audio id="musica" loop>
    <source src="sjjm_S_132.mp3" type="audio/mp3">
</audio>

<button class="music-btn" onclick="toggleMusic()">🎵</button>

<script>
const fecha = new Date("Oct 10, 2026 20:00:00").getTime();

function actualizarContador() {
    const ahora = new Date().getTime();
    const d = fecha - ahora;

    if (d > 0) {
        document.getElementById("dias").innerText = Math.floor(d/(1000*60*60*24));
        document.getElementById("horas").innerText = Math.floor((d%(1000*60*60*24))/(1000*60*60));
        document.getElementById("minutos").innerText = Math.floor((d%(1000*60*60))/(1000*60));
        document.getElementById("segundos").innerText = Math.floor((d%(1000*60))/1000);
    }
}

setInterval(actualizarContador, 1000);
actualizarContador();

function entrar(){
    const overlay = document.getElementById("overlay");
    overlay.style.opacity = "0";
    setTimeout(() => {
        overlay.style.display = "none";
    }, 800);
    
    const audio = document.getElementById("musica");
    audio.play().catch(error => console.log("Permiso de audio requerido."));
}

function zoom(img){
    document.getElementById("modal").style.display = "flex";
    document.getElementById("imgZoom").src = img.src;
}

function cerrar(){
    document.getElementById("modal").style.display = "none";
}

function toggleMusic(){
    let audio = document.getElementById("musica");
    audio.paused ? audio.play() : audio.pause();
}

const observerOptions = { threshold: 0.1 };
const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
        if (entry.isIntersecting) {
            entry.target.classList.add('show');
        }
    });
}, observerOptions);

document.querySelectorAll('.fade').forEach(el => observer.observe(el));
</script>

</body>
</html>


