# game
game
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Catch the Button</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      margin-top: 50px;
      background: #f0f8ff;
    }

    #gameButton {
      position: absolute;
      padding: 15px 25px;
      font-size: 18px;
      cursor: pointer;
      display: none;
    }

    #startBtn {
      padding: 10px 20px;
      font-size: 18px;
    }
  </style>
</head>
<body>

  <h1>🎯 Catch the Button!</h1>
  <p>Score: <span id="score">0</span></p>
  <p>Time left: <span id="time">10</span> seconds</p>

  <button id="startBtn">Start Game</button>
  <button id="gameButton">Click me!</button>

  <script>
    let score = 0;
    let timeLeft = 10;
    let timer;

    const gameButton = document.getElementById("gameButton");
    const startBtn = document.getElementById("startBtn");
    const scoreDisplay = document.getElementById("score");
    const timeDisplay = document.getElementById("time");

    function moveButton() {
      const x = Math.random() * (window.innerWidth - 100);
      const y = Math.random() * (window.innerHeight - 100);
      gameButton.style.left = x + "px";
      gameButton.style.top = y + "px";
    }

    gameButton.onclick = () => {
      score++;
      scoreDisplay.textContent = score;
      moveButton();
    };

    startBtn.onclick = () => {
      score = 0;
      timeLeft = 10;
      scoreDisplay.textContent = score;
      timeDisplay.textContent = timeLeft;
      gameButton.style.display = "block";
      moveButton();

      timer = setInterval(() => {
        timeLeft--;
        timeDisplay.textContent = timeLeft;

        if (timeLeft === 0) {
          clearInterval(timer);
          gameButton.style.display = "none";
          alert("Game Over! Your score: " + score);
        }
      }, 1000);
    };
  </script>

</body>
</html>
