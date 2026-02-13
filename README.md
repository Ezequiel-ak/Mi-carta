# Mi-carta
Mi 14
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Carta Romántica Premium</title>

<style>
body{
    margin:0;
    font-family:'Georgia', serif;
    background:linear-gradient(135deg,#ff4e8a,#ff99c8);
    overflow:hidden;
}

/* Luz suave cinematográfica */
body::after{
    content:"";
    position:fixed;
    width:200%;
    height:200%;
    background:radial-gradient(circle at center, rgba(255,255,255,0.25), transparent 60%);
    animation:lightMove 10s ease-in-out infinite alternate;
}
@keyframes lightMove{
    from{transform:translate(-5%,-5%) scale(1);}
    to{transform:translate(0%,0%) scale(1.1);}
}

/* ESCENA */
.scene{
    width:100%;
    height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;
    perspective:1500px;
    position:relative;
    z-index:2;
}

/* SOBRE */
.envelope{
    width:320px;
    height:200px;
    position:relative;
    transform-style:preserve-3d;
    cursor:pointer;
    transition:all 1.5s ease;
}

.base{
    width:100%;
    height:100%;
    background:white;
    border-radius:12px;
    box-shadow:0 20px 60px rgba(0,0,0,0.4);
    position:absolute;
}

.flap{
    width:100%;
    height:100%;
    background:#ffe6f0;
    position:absolute;
    transform-origin:top;
    transition:transform 1.2s ease;
    clip-path:polygon(0 0,100% 0,50% 65%);
}

.label{
    position:absolute;
    width:100%;
    height:100%;
    display:flex;
    justify-content:center;
    align-items:center;
    color:#e91e63;
    font-weight:bold;
    text-align:center;
}

.envelope.open .flap{
    transform:rotateX(-180deg);
}

.envelope.fadeOut{
    transform:scale(4);
    opacity:0;
}

/* INTERIOR */
.inside{
    position:absolute;
    width:100%;
    height:100vh;
    background:white;
    top:0;
    left:0;
    opacity:0;
    transition:opacity 2s ease;
    display:flex;
    flex-direction:column;
    align-items:center;
    padding-top:80px;
    overflow-y:auto;
}

.inside.show{
    opacity:1;
}

/* RAMO SVG */
.bouquet{
    width:180px;
    height:220px;
    position:relative;
    margin-bottom:30px;
    filter: drop-shadow(0 15px 20px rgba(0,0,0,0.25));
}

/* Tulipanes animación */
.tulip{
    position:absolute;
    width:40px;
    opacity:0;
    animation:enter 2s ease forwards;
}

@keyframes enter{
    from{
        transform:translateY(-300px) scale(0.3);
        opacity:0;
    }
    to{
        transform:translateY(0) scale(1);
        opacity:1;
    }
}

/* TEXTO */
.text{
    width:85%;
    max-width:600px;
    opacity:0;
    transform:translateY(40px);
    animation:fadeText 2.5s ease forwards 3s;
    color:#444;
    font-size:17px;
    line-height:1.8;
    text-align:center;
}

@keyframes fadeText{
    to{
        opacity:1;
        transform:translateY(0);
    }
}
</style>
</head>
<body>

<div class="scene">
    <div class="envelope" id="envelope" onclick="openLetter()">
        <div class="base"></div>
        <div class="flap"></div>
        <div class="label">💌 Abre la carta amor ❤️</div>
    </div>
</div>

<div class="inside" id="inside">

    <!-- RAMO BASE -->
    <div class="bouquet" id="bouquet">
        <!-- Papel del ramo -->
        <svg viewBox="0 0 200 250" width="180">
            <defs>
                <linearGradient id="paperGrad" x1="0" y1="0" x2="0" y2="1">
                    <stop offset="0%" stop-color="#fff0f5"/>
                    <stop offset="100%" stop-color="#ffd6e8"/>
                </linearGradient>
            </defs>
            <polygon points="40,80 160,80 100,230"
                     fill="url(#paperGrad)"
                     stroke="#f8a5c2"
                     stroke-width="3"/>
        </svg>
    </div>

    <div class="text">
        Han pasado 5 meses desde que nuestras vidas se unieron, y cada día sé que eres el hombre de mi vida ❤️.
        <br><br>
        Estás en cada pensamiento y en cada latido de mi corazón; tu presencia ilumina mis días como un rayo de sol ☀️💖.
        <br><br>
        Me haces sentir la chica más amada del mundo con tus mensajes, llamadas y palabras de amor 💌.
        <br><br>
        Eres atento, cariñoso y siempre logras hacerme sonreír.
        <br><br>
        Estoy orgullosa de nosotros y de nuestra relación.
        Eres mi compañero, mi amigo, mi confidente y mi todo 💞.
        <br><br>
        Te amo más de lo que las palabras pueden expresar 💕✨.
    </div>
</div>

<audio id="music" src="musica.mp3"></audio>

<script>
function openLetter(){
    const envelope=document.getElementById("envelope");
    envelope.classList.add("open");
    document.getElementById("music").play();

    setTimeout(()=>{
        envelope.classList.add("fadeOut");
    },1200);

    setTimeout(()=>{
        document.getElementById("inside").classList.add("show");
        createTulips();
    },2000);
}

function createTulips(){
    const bouquet=document.getElementById("bouquet");

    for(let i=0;i<5;i++){
        let svg=document.createElementNS("http://www.w3.org/2000/svg","svg");
        svg.setAttribute("viewBox","0 0 50 80");
        svg.setAttribute("class","tulip");
        svg.style.left=(40 + i*20)+"px";
        svg.style.top="20px";

        svg.innerHTML=`
        <defs>
            <linearGradient id="petalGrad${i}" x1="0" y1="0" x2="0" y2="1">
                <stop offset="0%" stop-color="#ff4e8a"/>
                <stop offset="100%" stop-color="#c2185b"/>
            </linearGradient>
        </defs>
        <path d="M25 10 C10 30, 15 50, 25 60 C35 50, 40 30, 25 10"
              fill="url(#petalGrad${i})"/>
        <rect x="23" y="60" width="4" height="20" fill="#2e7d32"/>
        `;

        bouquet.appendChild(svg);
    }
}
</script>

</body>
</html>
