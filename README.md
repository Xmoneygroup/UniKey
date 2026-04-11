<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>XStore 3D</title>
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;600;800&display=swap" rel="stylesheet">

<style>
*{margin:0;padding:0;box-sizing:border-box;font-family:'Orbitron',sans-serif;}
body{background:#050505;color:#fff;overflow:hidden;}

header{
  position:absolute;
  width:100%;
  display:flex;
  justify-content:space-between;
  padding:20px 50px;
  z-index:10;
}

.logo span{color:#ff3c00;text-shadow:0 0 15px #ff3c00;}
nav a{margin:0 15px;color:#aaa;text-decoration:none;}
nav a:hover{color:#fff;text-shadow:0 0 10px #ff3c00;}

.btn{border:1px solid #ff3c00;padding:8px 15px;border-radius:8px;color:#fff;text-decoration:none;}
.btn:hover{background:#ff3c00;box-shadow:0 0 10px #ff3c00;}

#canvas{
  width:100vw;
  height:100vh;
  display:block;
}

.overlayUI{
  position:absolute;
  bottom:50px;
  left:50%;
  transform:translateX(-50%);
  text-align:center;
}

.overlayUI h1 span{
  color:#ff3c00;
  text-shadow:0 0 20px #ff3c00;
}

.cta{
  margin-top:20px;
  padding:12px 30px;
  border:2px solid #ff3c00;
  background:transparent;
  color:#fff;
  border-radius:25px;
  cursor:pointer;
}

.cta:hover{
  background:#ff3c00;
  box-shadow:0 0 20px #ff3c00;
}
</style>
</head>

<body>

<header>
  <div class="logo"><span>X</span>STORE</div>
  <nav>
    <a href="#">Car Parts</a>
    <a href="#">Accessories</a>
    <a href="#">Performance</a>
    <a href="#">Services</a>
  </nav>
  <a href="#" class="btn">Login</a>
</header>

<canvas id="canvas"></canvas>

<div class="overlayUI">
  <h1><span>X</span>STORE 3D</h1>
  <button class="cta">ENTER STORE</button>
</div>

<script src="https://cdn.jsdelivr.net/npm/three@0.158.0/build/three.min.js"></script>
<script>
const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera(75, window.innerWidth/window.innerHeight, 0.1, 1000);
const renderer = new THREE.WebGLRenderer({canvas:document.getElementById('canvas'), antialias:true});
renderer.setSize(window.innerWidth, window.innerHeight);

// Lighting
const light = new THREE.PointLight(0xff3c00, 2, 100);
light.position.set(5,5,5);
scene.add(light);

const ambient = new THREE.AmbientLight(0xffffff, 0.3);
scene.add(ambient);

// Car placeholder (box as demo)
const geometry = new THREE.BoxGeometry(3,1,6);
const material = new THREE.MeshStandardMaterial({
  color:0x111111,
  emissive:0xff3c00,
  emissiveIntensity:0.2,
  metalness:1,
  roughness:0.2
});

const car = new THREE.Mesh(geometry, material);
scene.add(car);

camera.position.z = 10;

// Mouse interaction
let mouseX = 0;
document.addEventListener('mousemove', (e)=>{
  mouseX = (e.clientX / window.innerWidth - 0.5) * 2;
});

function animate(){
  requestAnimationFrame(animate);
  car.rotation.y += 0.01;
  car.rotation.x = mouseX * 0.3;
  renderer.render(scene, camera);
}

animate();

window.addEventListener('resize', ()=>{
  camera.aspect = window.innerWidth/window.innerHeight;
  camera.updateProjectionMatrix();
  renderer.setSize(window.innerWidth, window.innerHeight);
});
</script>

</body>
</html>
