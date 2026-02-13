# Mi-carta
Mi 14
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>14 de Febrero ❤️</title>

<style>
*{
  margin:0;
  padding:0;
  box-sizing:border-box;
  font-family:'Segoe UI',sans-serif;
}

body{
  height:100vh;
  background:linear-gradient(135deg,#ff9ecf,#ffc1e3);
  overflow:hidden;
  display:flex;
  justify-content:center;
  align-items:center;
  perspective:1200px;
}

/* SOBRE 3D */

.envelope{
  width:320px;
  height:220px;
  position:relative;
  cursor:pointer;
  transition:transform 1.2s ease;
  transform-style:preserve-3d;
}

.base{
  width:100%;
  height:100%;
  background:#ff5fa2;
  border-radius:8px;
  box-shadow:0 20px 40px rgba(0,0,0,0.25);
  position:absolute;
}

.flap{
  width:100%;
  height:100%;
  background:linear-gradient(to bottom,#ff77b7,#ff3d95);
  position:absolute;
  clip-path:polygon(0 0,100% 0,50% 55%);
  transform-origin:top;
  transition:transform 1.2s ease;
  box-shadow:0 8px 20px rgba(0,0,0,0.2);
}

.open .flap{
  transform:rotateX(-180deg);
}

/* TRANSICIÓN CINEMATOGRÁFICA */

.scene{
  position:absolute;
  width:100%;
  height:100%;
  background:linear-gradient(180deg,#ff9ecf,#ffd6ec);
  display:flex;
  justify-content:center;
  align-items:center;
  flex-direction:column;
  opacity:0;
  transform:scale(1.3);
  transition:all 1.5s ease;
  backdrop-filter:blur(8px);
}

.scene.show{
  opacity:1;
  transform:scale(1);
}

/* RAMO SVG */

.bouquet{
  width:200px;
  margin-bottom:20px;
  opacity:0;
  transform:translateY(50px) scale(.8);
  transition:1.5s ease;
}

.bouquet.show{
  opacity:1;
  transform:translateY(0) scale(1);
}

/* TEXTO DESLIZABLE */

.letter{
  width:85%;
  max-width:420px;
  max-height:45vh;
  overflow-y:auto;
  background:white;
  padding:20px;
  border-radius:16px;
  box-shadow:0 10px 40px rgba(0,0,0,0.2);
  opacity:0;
  transform:translateY(60px);
  transition:1.5s ease;
}

.letter.show{
  opacity:1;
  transform:translateY(0);
}

.letter p{
  line-height:1.6;
  color:#444;
  font-size:15px;
}

/* SCROLL SUAVE */

.letter::-webkit-scrollbar{
  width:6px;
}
.letter::-webkit-scrollbar-thumb{
  background:#ff6fb3;
  border-radius:4px;
}

/* PÉTALOS 3D */

.petals{
  position:absolute;
  width:100%;
  height:100%;
  pointer-events:none;
  overflow:hidden;
}

.petal{
  position:absolute;
  width:18px;
  height:24px;
  background:radial-gradient(circle at 30% 30%,#ffb3d9,#ff2a84);
  border-radius:50% 50% 50% 50%;
  box-shadow:0 0 10px rgba(255,0,100,0.5);
  animation:fall 8s linear infinite;
  transform-style:preserve-3d;
}

@keyframes fall{
  0%{transform:translateY(-50px) rotateY(0deg) rotateX(0deg);}
  100%{transform:translateY(110vh) rotateY(360deg) rotateX(360deg);}
}

.title{
  position:absolute;
  top:15%;
  color:white;
  font-size:20px;
  font-weight:bold;
  text-shadow:0 4px 10px rgba(0,0,0,0.3);
}

</style>
</head>
<body>

<div class="title">Abre la carta amor ❤️</div>

<div class="envelope" onclick="openLetter()">
  <div class="base"></div>
  <div class="flap"></div>
</div>

<div class="scene" id="scene">

  <!-- RAMO SVG REALISTA -->
  <svg class="bouquet" id="bouquet" viewBox="0 0 200 250">
    <defs>
      <linearGradient id="petalGrad" x1="0%" y1="0%" x2="100%" y2="100%">
        <stop offset="0%" stop-color="#ffb6d9"/>
        <stop offset="100%" stop-color="#ff007a"/>
      </linearGradient>
      <linearGradient id="stemGrad" x1="0%" y1="0%" x2="0%" y2="100%">
        <stop offset="0%" stop-color="#4caf50"/>
        <stop offset="100%" stop-color="#2e7d32"/>
      </linearGradient>
    </defs>

    <!-- Tallos -->
    <rect x="90" y="120" width="6" height="100" fill="url(#stemGrad)"/>
    <rect x="70" y="130" width="6" height="90" fill="url(#stemGrad)"/>
    <rect x="110" y="130" width="6" height="90" fill="url(#stemGrad)"/>

    <!-- Tulipanes -->
    <ellipse cx="93" cy="110" rx="20" ry="30" fill="url(#petalGrad)"/>
    <ellipse cx="73" cy="120" rx="18" ry="28" fill="url(#petalGrad)"/>
    <ellipse cx="113" cy="120" rx="18" ry="28" fill="url(#petalGrad)"/>
  </svg>

  <!-- CARTA -->
  <div class="letter" id="letter">
    <p>
    Han pasado 5 meses desde que nuestras vidas se unieron, y cada día sé que eres el hombre de mi vida ❤️.
    Estás en cada pensamiento y en cada latido de mi corazón; tu presencia ilumina mis días como un rayo de sol ☀️💖.
    Me haces sentir la chica más amada del mundo con tus mensajes, llamadas y palabras de amor 💌.
    Eres atento, cariñoso y siempre logras hacerme sonreír.
    Estoy orgullosa de nosotros y de nuestra relación.
    Eres mi compañero, mi amigo, mi confidente y mi todo 💞.
    Eres el hombre de mis sueños, mi alma gemela, y contigo siento que puedo conquistar el mundo.
    Te amo más de lo que las palabras pueden expresar 💕✨.
    </p>
  </div>

</div>

<div class="petals" id="petals"></div>

<audio id="music" src="musica.mp3"></audio>

<script>

function openLetter(){
  document.querySelector('.envelope').classList.add('open');
  document.getElementById('music').play();

  setTimeout(()=>{
    document.querySelector('.envelope').style.display="none";
    document.querySelector('.title').style.display="none";
    document.getElementById('scene').classList.add('show');
    document.getElementById('bouquet').classList.add('show');
    document.getElementById('letter').classList.add('show');
    createPetals();
  },1200);
}

function createPetals(){
  const container=document.getElementById('petals');
  for(let i=0;i<20;i++){
    let petal=document.createElement('div');
    petal.classList.add('petal');
    petal.style.left=Math.random()*100+"vw";
    petal.style.animationDuration=(6+Math.random()*5)+"s";
    container.appendChild(petal);
  }
}

</script>

</body>
</html>
