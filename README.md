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
  background:linear-gradient(135deg,#ff9ac9,#ffc8e6);
  display:flex;
  justify-content:center;
  align-items:center;
  overflow:hidden;
  perspective:1500px;
}

/* SOBRE */

.envelope{
  width:320px;
  height:200px;
  position:relative;
  cursor:pointer;
  transform-style:preserve-3d;
  transition:1.2s;
}

.base{
  position:absolute;
  width:100%;
  height:100%;
  background:#ff4d94;
  border-radius:10px;
  box-shadow:0 20px 40px rgba(0,0,0,0.3);
}

.flap{
  position:absolute;
  width:100%;
  height:100%;
  background:linear-gradient(to bottom,#ff6fb3,#ff2a7f);
  clip-path:polygon(0 0,100% 0,50% 55%);
  transform-origin:top;
  transition:1.2s;
}

.open .flap{
  transform:rotateX(-180deg);
}

.title{
  position:absolute;
  top:18%;
  color:white;
  font-size:20px;
  font-weight:bold;
  text-shadow:0 4px 10px rgba(0,0,0,0.4);
}

/* ESCENA INTERIOR */

.scene{
  position:absolute;
  inset:0;
  display:flex;
  flex-direction:column;
  align-items:center;
  justify-content:center;
  opacity:0;
  transform:scale(1.2);
  transition:1.5s ease;
}

.scene.show{
  opacity:1;
  transform:scale(1);
}

/* RAMO */

.bouquet{
  width:200px;
  margin-bottom:20px;
  filter:drop-shadow(0 15px 25px rgba(0,0,0,0.3));
  opacity:0;
  transform:translateY(50px);
  transition:1.5s ease;
}

.bouquet.show{
  opacity:1;
  transform:translateY(0);
}

/* CARTA */

.letter{
  width:85%;
  max-width:420px;
  max-height:45vh;
  overflow-y:auto;
  background:white;
  padding:22px;
  border-radius:18px;
  box-shadow:0 20px 50px rgba(0,0,0,0.25);
  opacity:0;
  transform:translateY(40px);
  transition:1.5s ease;
}

.letter.show{
  opacity:1;
  transform:translateY(0);
}

.letter p{
  font-size:15px;
  line-height:1.7;
  color:#444;
}

/* SCROLL SOLO EN TEXTO */

.letter::-webkit-scrollbar{
  width:6px;
}
.letter::-webkit-scrollbar-thumb{
  background:#ff5fa2;
  border-radius:10px;
}

/* PÉTALOS */

.petals{
  position:absolute;
  inset:0;
  pointer-events:none;
  overflow:hidden;
}

.petal{
  position:absolute;
  width:16px;
  height:22px;
  background:radial-gradient(circle at 30% 30%,#ffb3d9,#ff0066);
  border-radius:50%;
  box-shadow:0 5px 15px rgba(0,0,0,0.3);
  animation:fall linear infinite;
}

@keyframes fall{
  0%{
    transform:translateY(-10vh) rotate(0deg);
    opacity:1;
  }
  100%{
    transform:translateY(110vh) rotate(360deg);
    opacity:0.8;
  }
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

  <rect x="90" y="120" width="6" height="100" fill="url(#stemGrad)"/>
  <rect x="70" y="130" width="6" height="90" fill="url(#stemGrad)"/>
  <rect x="110" y="130" width="6" height="90" fill="url(#stemGrad)"/>

  <ellipse cx="93" cy="110" rx="20" ry="30" fill="url(#petalGrad)"/>
  <ellipse cx="73" cy="120" rx="18" ry="28" fill="url(#petalGrad)"/>
  <ellipse cx="113" cy="120" rx="18" ry="28" fill="url(#petalGrad)"/>
</svg>

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
  for(let i=0;i<15;i++){
    let petal=document.createElement('div');
    petal.className='petal';
    petal.style.left=Math.random()*100+'vw';
    petal.style.animationDuration=(5+Math.random()*4)+'s';
    container.appendChild(petal);
  }
}

</script>

</body>
</html>
