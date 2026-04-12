<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Premium Galaxy</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      overflow: hidden;
      background: black;
      font-family: Arial, sans-serif;
      color: white;
    }

    canvas {
      position: fixed;
      top: 0;
      left: 0;
      z-index: -1;
    }

    .content {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      text-align: center;
    }

    h1 {
      font-size: 4rem;
      letter-spacing: 2px;
      background: linear-gradient(90deg, #fff, #888, #fff);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      animation: glow 3s infinite alternate;
    }

    @keyframes glow {
      from {
        text-shadow: 0 0 10px #fff;
      }
      to {
        text-shadow: 0 0 30px #00ccff, 0 0 60px #6600ff;
      }
    }

    p {
      margin-top: 20px;
      opacity: 0.7;
    }
  </style>
</head>
<body>

<canvas id="galaxy"></canvas>

<div class="content">
  <h1>PREMIUM DOMAIN</h1>
  <p>Future digital asset</p>
</div>

<script>
  const canvas = document.getElementById("galaxy");
  const ctx = canvas.getContext("2d");

  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;

  let stars = [];

  class Star {
    constructor() {
      this.x = Math.random() * canvas.width;
      this.y = Math.random() * canvas.height;
      this.radius = Math.random() * 1.5;
      this.speed = Math.random() * 0.5;
    }

    draw() {
      ctx.beginPath();
      ctx.arc(this.x, this.y, this.radius, 0, Math.PI * 2);
      ctx.fillStyle = "white";
      ctx.fill();
    }

    update() {
      this.y += this.speed;
      if (this.y > canvas.height) {
        this.y = 0;
        this.x = Math.random() * canvas.width;
      }
      this.draw();
    }
  }

  function init() {
    for (let i = 0; i < 300; i++) {
      stars.push(new Star());
    }
  }

  function animate() {
    ctx.fillStyle = "rgba(0, 0, 20, 0.3)";
    ctx.fillRect(0, 0, canvas.width, canvas.height);

    stars.forEach(star => star.update());

    requestAnimationFrame(animate);
  }

  init();
  animate();

  window.addEventListener("resize", () => {
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
  });
</script>

</body>
</html>
