# Kazan
<!DOCTYPE html><html lang="tr">
<head>
  <meta charset="UTF-8">
  <title>JetX Basit Uygulama</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: radial-gradient(ellipse at center, #0d1b2a, #000);
      color: white;
      text-align: center;
      overflow: hidden;
    }
    #rocket {
      position: absolute;
      left: 20%;
      top: 60%;
      transition: top 0.2s;
      width: 60px;
    }
    #multiplier {
      font-size: 48px;
      color: #ffff00;
      margin-top: 100px;
    }
    .buttons {
      margin-top: 50px;
    }
    .btn {
      padding: 10px 20px;
      margin: 10px;
      font-size: 20px;
      cursor: pointer;
      border: none;
      border-radius: 10px;
    }
    .bet {
      background-color: green;
      color: white;
    }
    .cashout {
      background-color: orange;
      color: black;
    }
  </style>
</head>
<body>
  <img id="rocket" src="https://upload.wikimedia.org/wikipedia/commons/e/e7/Rocket_emoji.png" alt="Rocket">
  <div id="multiplier">x1.00</div>
  <div class="buttons">
    <button class="btn bet" onclick="startGame()">BAHİS YAP</button>
    <button class="btn cashout" onclick="cashOut()">ERKEN ÇIK</button>
  </div>  <script>
    let multiplier = 1.00;
    let interval;
    let isRunning = false;
    let rocket = document.getElementById("rocket");

    function startGame() {
      multiplier = 1.00;
      isRunning = true;
      rocket.style.top = '60%';
      interval = setInterval(() => {
        multiplier += 0.05 + Math.random() * 0.1;
        document.getElementById("multiplier").innerText = "x" + multiplier.toFixed(2);
        rocket.style.top = (parseFloat(rocket.style.top) - 1) + '%';

        // Simulate random crash
        if (Math.random() < 0.01 + multiplier / 200) {
          clearInterval(interval);
          isRunning = false;
          alert("PATLADI! Çarpan: x" + multiplier.toFixed(2));
        }
      }, 100);
    }

    function cashOut() {
      if (isRunning) {
        clearInterval(interval);
        isRunning = false;
        alert("ERKEN ÇIKTIN! Kazanç: x" + multiplier.toFixed(2));
      }
    }
  </script></body>
</html>
