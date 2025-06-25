<!DOCTYPE html><html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Simulasi Slot</title>
  <style>
    body {
      text-align: center;
      font-family: sans-serif;
      background: linear-gradient(to right, #1f1f1f, #2a2a2a);
      color: #fff;
      padding-top: 50px;
    }
    #reels {
      font-size: 60px;
      margin: 20px;
      letter-spacing: 20px;
      transition: transform 0.3s ease-in-out;
    }
    #spin {
      padding: 12px 40px;
      font-size: 22px;
      background: gold;
      border: none;
      border-radius: 10px;
      cursor: pointer;
      box-shadow: 0 4px 8px rgba(0,0,0,0.5);
      transition: transform 0.2s;
    }
    #spin:active {
      transform: scale(0.95);
    }
    #saldo {
      margin-top: 20px;
      font-size: 18px;
    }
  </style>
</head>
<body>
  <h1>🎰 Simulasi Slot</h1>
  <div id="reels">🍒 🍋 🍇</div>
  <button id="spin">SPIN</button>
  <div id="saldo">Saldo: 1000</div>  <!-- Suara --><audio id="spinSound" src="https://www.myinstants.com/media/sounds/slot-machine.mp3"></audio> <audio id="winSound" src="https://www.myinstants.com/media/sounds/tada-fanfare.mp3"></audio>

  <script>
    const symbols = ["🍒", "🍋", "🍇", "🔔", "7️⃣"];
    const reels = document.getElementById("reels");
    const saldoDiv = document.getElementById("saldo");
    const spinSound = document.getElementById("spinSound");
    const winSound = document.getElementById("winSound");
    let saldo = 1000;

    document.getElementById("spin").onclick = () => {
      spinSound.currentTime = 0;
      spinSound.play();

      // Animasi spin
      reels.style.transform = "scale(1.2) rotate(10deg)";
      setTimeout(() => {
        reels.style.transform = "scale(1) rotate(0deg)";

        const s1 = symbols[Math.floor(Math.random() * symbols.length)];
        const s2 = symbols[Math.floor(Math.random() * symbols.length)];
        const s3 = symbols[Math.floor(Math.random() * symbols.length)];
        reels.textContent = `${s1} ${s2} ${s3}`;

        if (s1 === s2 && s2 === s3) {
          saldo += 500;
          winSound.currentTime = 0;
          winSound.play();
          alert("🎉 Jackpot! +500");
        } else {
          saldo -= 50;
        }
        saldoDiv.textContent = `Saldo: ${saldo}`;
      }, 500);
    };
  </script></body>
</html>
