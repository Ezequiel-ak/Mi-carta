# Mi-carta
Mi 14
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>San Valentín 3D 💘</title>
<style>
body{
  margin:0;
  overflow:hidden;
  background:#000;
}
#overlay{
  position:absolute;
  top:10%;
  width:100%;
  text-align:center;
  font-size:40px;
  color:#ff6fa5;
  font-family:cursive;
  z-index:2;
}
</style>
</head>
<body>

<div id="overlay">¿Quieres ser mi San Valentín? 💕</div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r152/three.min.js"></script>

<script>

let scene = new THREE.Scene();
scene.background = new THREE.Color(0xffd6ec);

let camera = new THREE.PerspectiveCamera(60, window.innerWidth/window.innerHeight, 0.1, 1000);
camera.position.z = 6;

let renderer = new THREE.WebGLRenderer({antialias:true});
renderer.setSize(window.innerWidth, window.innerHeight);
document.body.appendChild(renderer.domElement);

/* LUCES */

let light = new THREE.PointLight(0xff99cc, 2, 100);
light.position.set(5,5,5);
scene.add(light);

let ambient = new THREE.AmbientLight(0xffffff, 0.6);
scene.add(ambient);

/* SOBRE 3D */

let baseGeometry = new THREE.BoxGeometry(3,2,0.2);
let material = new THREE.MeshStandardMaterial({color:0xff4d94});
let envelope = new THREE.Mesh(baseGeometry, material);
scene.add(envelope);

let flapGeometry = new THREE.BoxGeometry(3,1,0.1);
let flap = new THREE.Mesh(flapGeometry, material);
flap.position.y = 1.5;
scene.add(flap);

/* CORAZONES FONDO */

let hearts = [];
let heartGeo = new THREE.SphereGeometry(0.1,16,16);
let heartMat = new THREE.MeshStandardMaterial({color:0xff007a});

for(let i=0;i<100;i++){
  let heart = new THREE.Mesh(heartGeo,heartMat);
  heart.position.set(
    (Math.random()-0.5)*20,
    (Math.random()-0.5)*20,
    (Math.random()-0.5)*20
  );
  scene.add(heart);
  hearts.push(heart);
}

/* ANIMACIÓN */

let opened = false;

window.addEventListener("click",()=>{

  if(!opened){
    opened = true;

    // abrir sobre
    flap.rotation.x = -Math.PI/1.5;

    // cámara entra
    setTimeout(()=>{
      camera.position.z = 2;
    },1000);

  }

});

function animate(){
  requestAnimationFrame(animate);

  hearts.forEach(h=>{
    h.rotation.y += 0.01;
  });

  renderer.render(scene,camera);
}

animate();

</script>

</body>
</html>
