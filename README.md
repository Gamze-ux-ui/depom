<!DOCTYPE html>
<html lang="tr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>NEVA Dans Sahnesi</title>  bu koda qr kod yapmalıyım 
  <style>
    body {
      margin: 0;
      height: 100vh;
      overflow: hidden;
      display: flex;
      align-items: center;
      justify-content: center;
      position: relative;
      background: radial-gradient(circle at center, #000011, #000000);
    }

    /* Yıldızlı arka plan için particles */
    .stars {
      position: absolute;
      width: 100%;
      height: 100%;
      background: transparent;
      z-index: 0;
    }

    canvas {
      position: absolute;
      top: 0;
      left: 0;
      z-index: 0;
    }

    .neva-container {
      display: flex;
      gap: 20px;
      font-family: 'Pacifico', cursive;
      font-size: 80px;
      color: #fff88a;
      z-index: 1;
    }

    .letter {
      opacity: 0;
      animation-fill-mode: forwards;
      text-shadow: 0 0 10px #fff88a;
    }

    @keyframes enterA {
      0% { transform: translateX(-600px) rotate(0deg); opacity: 0; }
      100% { transform: translateX(0) rotate(720deg); opacity: 1; }
    }

    @keyframes enterN {
      0% { transform: translateY(-500px) scale(0.2); opacity: 0; }
      100% { transform: translateY(0) scale(1); opacity: 1; }
    }

    @keyframes enterE {
      0% { transform: translateX(600px) rotateX(720deg); opacity: 0; }
      100% { transform: translateX(0) rotateX(0deg); opacity: 1; }
    }

    @keyframes enterV {
      0% { transform: translateY(500px) skewX(45deg); opacity: 0; }
      100% { transform: translateY(0) skewX(0deg); opacity: 1; }
    }

    @keyframes danceA {
      0% { transform: scale(1) rotate(0deg); }
      25% { transform: rotate(20deg) scale(1.2); }
      50% { transform: rotate(-20deg) scale(0.8); }
      75% { transform: rotate(10deg); }
      100% { transform: rotate(0deg) scale(1); }
    }

    @keyframes danceN {
      0% { transform: translateY(0); }
      20% { transform: translateY(-20px) rotate(10deg); }
      40% { transform: translateY(20px) rotate(-10deg); }
      60% { transform: scale(1.1); }
      80% { transform: scale(0.9); }
      100% { transform: translateY(0) rotate(0deg) scale(1); }
    }

    @keyframes danceE {
      0% { transform: scale(1); }
      25% { transform: scale(1.3); }
      50% { transform: rotateY(180deg); }
      75% { transform: rotateY(0deg); }
      100% { transform: scale(1); }
    }

    @keyframes danceV {
      0% { transform: rotate(0deg); }
      20% { transform: rotate(360deg); }
      40% { transform: scale(1.2); }
      60% { transform: scale(0.8); }
      80% { transform: translateX(-10px); }
      100% { transform: translateX(0); }
    }

    @keyframes glow {
      0%, 100% { text-shadow: 0 0 10px #fff88a, 0 0 20px #fff88a; }
      50% { text-shadow: 0 0 30px #ffffc0, 0 0 60px #ffffc0; }
    }

    .letter.n { animation: enterN 1s ease-out 0s forwards, danceN 2s ease-in-out 1s infinite, glow 2s infinite 3s; }
    .letter.e { animation: enterE 1s ease-out 2s forwards, danceE 2s ease-in-out 3s infinite, glow 2s infinite 5s; }
    .letter.v { animation: enterV 1s ease-out 4s forwards, danceV 2s ease-in-out 5s infinite, glow 2s infinite 7s; }
    .letter.a { animation: enterA 1s ease-out 6s forwards, danceA 2s ease-in-out 7s infinite, glow 2s infinite 9s; }
  </style>
  <link href="https://fonts.googleapis.com/css2?family=Pacifico&display=swap" rel="stylesheet" />
</head>
<body>
  <canvas id="stars"></canvas>
  <div class="neva-container">
    <div class="letter n">N</div>
    <div class="letter e">E</div>
    <div class="letter v">V</div>
    <div class="letter a">A</div>
  </div>

  <script>
    // Yıldızlı arka plan canvas
    const canvas = document.getElementById('stars');
    const ctx = canvas.getContext('2d');
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

    const stars = [];
    for (let i = 0; i < 200; i++) {
      stars.push({
        x: Math.random() * canvas.width,
        y: Math.random() * canvas.height,
        radius: Math.random() * 1.5,
        alpha: Math.random(),
        dx: (Math.random() - 0.5) * 0.5,
        dy: (Math.random() - 0.5) * 0.5
      });
    }

    function drawStars() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      stars.forEach(star => {
        ctx.beginPath();
        ctx.arc(star.x, star.y, star.radius, 0, Math.PI * 2);
        ctx.fillStyle = rgba(255, 255, 200, ${star.alpha});
        ctx.fill();
        star.x += star.dx;
        star.y += star.dy;

        if (star.x < 0 || star.x > canvas.width) star.dx *= -1;
        if (star.y < 0 || star.y > canvas.height) star.dy *= -1;
      });
      requestAnimationFrame(drawStars);
    }

    drawStars();
  </script>
</body>
</html>


