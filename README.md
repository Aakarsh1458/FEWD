<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple Click Game</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #f0f0f0;
        }

        #gameContainer {
            text-align: center;
        }

        #score {
            font-size: 24px;
            margin-bottom: 20px;
        }

        #clickBox {
            width: 100px;
            height: 100px;
            background-color: #3498db;
            cursor: pointer;
            border-radius: 10px;
        }

        #gameOver {
            font-size: 30px;
            color: red;
            display: none;
        }
    </style>
</head>
<body>
    <div id="gameContainer">
        <div id="score">Score: 0</div>
        <div id="clickBox"></div>
        <div id="gameOver">Game Over!</div>
    </div>

    <script>
        let score = 0;
        const scoreDisplay = document.getElementById('score');
        const clickBox = document.getElementById('clickBox');
        const gameOverDisplay = document.getElementById('gameOver');

        clickBox.addEventListener('click', function() {
            score++;
            scoreDisplay.textContent = 'Score: ' + score;
            moveBox();
        });

        function moveBox() {
            const maxX = window.innerWidth - 120; // Box width + some margin
            const maxY = window.innerHeight - 120; // Box height + some margin

            const randomX = Math.floor(Math.random() * maxX);
            const randomY = Math.floor(Math.random() * maxY);

            clickBox.style.position = 'absolute';
            clickBox.style.left = randomX + 'px';
            clickBox.style.top = randomY + 'px';
        }

        
        setTimeout(function() {
            gameOverDisplay.style.display = 'block';
            clickBox.style.display = 'none';
        }, 30000);

        moveBox();
    </script>
</body>
</html>
