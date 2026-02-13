# Mi-carta
Mi 14
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>San Valentín 💘</title>

<link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Poppins:wght@300;400&display=swap" rel="stylesheet">

<style>
*{
  margin:0;
  padding:0;
  box-sizing:border-box;
}

body{
  height:100vh;
  overflow:hidden;
  background:#ffdde9;
  font-family:'Poppins',sans-serif;
  display:flex;
  justify-content:center;
  align-items:center;
}

/* FONDO CON CORAZONES */

body::before{
  content:"";
  position:absolute;
  inset:0;
  background:
    radial-gradient(circle at 20% 30%, rgba(255,0,100,0.2) 20px, transparent 21px),
    radial-gradient(circle at 70% 60%, rgba(255,0,100,0.15) 25px, transparent 26px),
    radial-gradient(circle at 40% 80%, rgba(255,0,100,0.2) 18px, transparent 19px);
  background-size:200px 200px;
  animation:moveBg 20s linear infinite;
}

@keyframes moveBg{
  from{background-position:0 0;}
  to{background-position:200px 200px;}
}

/* TEXTO INICIAL */

.intro{
  position:absolute;
  top:15%;
  font-family:'Great Vibes',cursive;
  font-size:42px;
  color:#d1005b;
  text-shadow:0 5px 15px rgba(0,0,0,0.2);
  animation:fadeIn 2s ease forwards;
}

@keyframes fadeIn{
  from{opacity:0; transform:translateY(-20px);}
  to{opacity:1; transform:translateY(0);}
}

/* CARTA CON ALAS */

.envelope{
  position:absolute;
  width:260px;
  height:170px;
  background:#ff4d94;
  border-radius:10px;
  box-shadow:0 20px 40px rgba(0,0,0,0.3);
  cursor:pointer;
  animation:flyIn 3s ease forwards, float 3s ease-in-out infinite 3s;
}

@keyframes flyIn{
  from{transform:translateY(-150vh) rotate(-10deg);}
  to{transform:translateY(0) rotate(0);}
}

@keyframes float{
  0%,100%{transform:translateY(0);}
  50%{transform:translateY(-15px);}
}

/* CORAZÓN FLECHADO */

.envelope::after{
  content:"💘";
  font-size:40px;
  position:absolute;
  top:50%;
  left:50%;
  transform:translate(-50%,-50%);
}

/* ALAS */

.wing{
  position:absolute;
  font-size:40px;
  top:40%;
}

.wing.left{
  left:-35px;
}

.wing.right{
  right:-35px;
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
  transition:1.5s ease;
}

.scene.show{
  opacity:1;
}

/* CARTA TEXTO */

.letter{
  width:85%;
  max-width:420px;
  max-height:50vh;
  overflow-y:auto;
  background:white;
  padding:25px;
  border-radius:20px;
  box-shadow:0 20px 50px rgba(0,0,0,0.25);
  font-size:15px;
  line-height:1.7;
}

.signature{
  margin-top:20px;
  font-weight:bold;
  text-align:right;
  color:#d1005b;
}

/* RAMO */

.bouquet{
  width:180px;
  margin-bottom:20px;
  animation:fadeUp 1.5s ease forwards;
}

@keyframes fadeUp{
  from{opacity:0; transform:translateY(40px);}
  to{opacity:1; transform:translateY(0);}
}

</style>
</head>
<body>

<div class="intro">¿Quieres ser mi San Valentín? 💕</div>

<div class="envelope" id="envelope">
  <div class="wing left">🕊</div>
  <div class="wing right">🕊</div>
</div>

<div class="scene" id="scene">

<svg class="bouquet" viewBox="0 0 200 250">
  <rect x="90" y="120" width="6" height="100" fill="#2e7d32"/>
  <rect x="70" y="130" width="6" height="90" fill="#2e7d32"/>
  <rect x="110" y="130" width="6" height="90" fill="#2e7d32"/>

  <ellipse cx="93" cy="110" rx="20" ry="30" fill="#ff007a"/>
  <ellipse cx="73" cy="120" rx="18" ry="28" fill="#ff4fa3"/>
  <ellipse cx="113" cy="120" rx="18" ry="28" fill="#ff4fa3"/>
</svg>

<div class="letter">
Han pasado 5 meses desde que nuestras vidas se unieron, y cada día sé que eres el hombre de mi vida ❤️.
Estás en cada pensamiento y en cada latido de mi corazón; tu presencia ilumina mis días como un rayo de sol ☀️💖.
Me haces sentir la chica más amada del mundo con tus mensajes, llamadas y palabras de amor 💌.
Eres atento, cariñoso y siempre logras hacerme sonreír.
Estoy orgullosa de nosotros y de nuestra relación.
Eres mi compañero, mi amigo, mi confidente y mi todo 💞.
Eres el hombre de mis sueños, mi alma gemela, y contigo siento que puedo conquistar el mundo.
Te amo más de lo que las palabras pueden expresar 💕✨.

<div class="signature">ATT Selena💘</div>
</div>

</div>

<script>

const envelope=document.getElementById("envelope");

envelope.addEventListener("click",function(){

  envelope.style.display="none";
  document.querySelector(".intro").style.display="none";

  document.getElementById("scene").classList.add("show");

});

</script>

</body>
</html>
