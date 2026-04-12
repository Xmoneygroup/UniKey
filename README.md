<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Ultra Premium Domain</title>

<style>
body {
  margin: 0;
  overflow: hidden;
  background: radial-gradient(circle at center, #050510, #000);
  font-family: Arial, sans-serif;
  color: white;
}

/* Glass UI */
.panel {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  padding: 40px 60px;
  backdrop-filter: blur(20px);
  background: rgba(255,255,255,0.05);
  border: 1px solid rgba(255,255,255,0.1);
  border-radius: 20px;
  text-align: center;
}

h1 {
  font-size: 4rem;
  letter-spacing: 3px;
}

p {
  opacity: 0.6;
}

button {
  margin-top: 20px;
  padding: 12px 30px;
  border-radius: 30px;
  border: none;
  background: linear-gradient(90deg, #00ccff, #6600ff);
  color: white;
  cursor: pointer;
  transition: 0.3s;
}

button:hover {
  transform: scale(1.1);
}
</style>
</head>

<body>

<div class="panel">
  <h1>PREMIUM DOMAIN</h1>
  <p>This domain is for sale</p>
  <button>Buy Now</button>
</div>

<script src="https://cdn.jsdelivr.net/npm/three@0.152.2/build/three.min.js"></script>

<script>
const scene = new THREE.Scene();

const camera = new THREE.PerspectiveCamera(
  75,
  window.innerWidth / window.innerHeight,
  0.1,
  2000
);

const renderer = new THREE.WebGLRenderer({ antialias: true });
renderer.setSize(window.innerWidth, window.innerHeight);
document.body.appendChild(renderer.domElement);

// 🌌 Spiral Galaxy
const particles = 15000;
const geometry = new THREE.BufferGeometry();
const positions = new Float32Array(particles * 3);

for (let i = 0; i < particles; i++) {
  const i3 = i * 3;

  const radius = Math.random() * 500;
  const angle = radius * 0.05;

  positions[i3] = Math.cos(angle) * radius;
  positions[i3 + 1] = (Math.random() - 0.5) * 50;
  positions[i3 + 2] = Math.sin(angle) * radius;
}

geometry.setAttribute(
  "position",
  new THREE.BufferAttribute(positions, 3)
);

const material = new THREE.PointsMaterial({
  size: 1.2,
  color: 0xffffff
});

const galaxy = new THREE.Points(geometry, material);
scene.add(galaxy);

camera.position.z = 200;

// 🖱️ Mouse interaction
let mouseX = 0;
let mouseY = 0;

document.addEventListener("mousemove", (e) => {
  mouseX = (e.clientX - window.innerWidth / 2) * 0.001;
  mouseY = (e.clientY - window.innerHeight / 2) * 0.001;
});

// 🎬 Animation
function animate() {
  requestAnimationFrame(animate);

  galaxy.rotation.y += 0.0008;

  camera.position.x += (mouseX * 50 - camera.position.x) * 0.05;
  camera.position.y += (-mouseY * 50 - camera.position.y) * 0.05;

  camera.lookAt(scene.position);

  renderer.render(scene, camera);
}

animate();

// 📱 Resize
window.addEventListener("resize", () => {
  camera.aspect = window.innerWidth / window.innerHeight;
  camera.updateProjectionMatrix();
  renderer.setSize(window.innerWidth, window.innerHeight);
});
</script>

</body>
</html>
