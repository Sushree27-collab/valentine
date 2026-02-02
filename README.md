<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Valentine 💖</title>

  <style>
    body {
      height: 100vh;
      margin: 0;
      overflow: hidden;
      display: flex;
      justify-content: center;
      align-items: center;
      background: #ffe6eb;
      font-family: Arial, sans-serif;
    }

    .card {
      background: white;
      padding: 30px 40px;
      border-radius: 20px;
      text-align: center;
      box-shadow: 0 10px 25px rgba(0,0,0,0.15);
      position: relative;
      z-index: 2;
    }

    h1 {
      color: #e6005c;
      margin-bottom: 25px;
    }

    button {
      padding: 12px 25px;
      font-size: 18px;
      border: none;
      border-radius: 12px;
      cursor: pointer;
      margin: 10px;
    }

    .yes {
      background: #ff4d88;
      color: white;
    }

    .no {
      background: #ccc;
      color: #555;
      position: absolute;
    }

    /* 💖 Hearts */
    .heart {
      position: fixed;
      top: -20px;
      font-size: 24px;
      animation: fall 4s linear forwards;
      color: #ff4d88;
      z-index: 1;
      pointer-events: none;
    }

    @keyframes fall {
      to {
        transform: translateY(110vh);
        opacity: 0;
      }
    }
  </style>
</head>

<body>

  <div class="card">
    <h1>Will you be my Valentine? 💖</h1>
    <button class="yes" onclick="sayYes()">Yes</button>
    <button class="no" onmouseover="runAway()">No</button>
  </div>

  <script>
    function sayYes() {
      startHearts();
      alert("Yayyy! 💕 I knew you'd say YES!");
    }

    function runAway() {
      const noBtn = document.querySelector('.no');
      const card = document.querySelector('.card');

      const maxX = card.clientWidth - noBtn.offsetWidth;
      const maxY = card.clientHeight - noBtn.offsetHeight;

      const x = Math.random() * maxX;
      const y = Math.random() * maxY;

      noBtn.style.left = x + 'px';
      noBtn.style.top = y + 'px';
    }

    function startHearts() {
      for (let i = 0; i < 40; i++) {
        createHeart();
      }
    }

    function createHeart() {
      const heart = document.createElement('div');
      heart.className = 'heart';
      heart.innerText = '💖';

      heart.style.left = Math.random() * 100 + 'vw';
      heart.style.animationDuration = (Math.random() * 2 + 3) + 's';
      heart.style.fontSize = (Math.random() * 20 + 20) + 'px';

      document.body.appendChild(heart);

      setTimeout(() => {
        heart.remove();
      }, 5000);
    }
  </script>

</body>
</html>
