<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple HTML Game</title>
    <style>
        body {
            margin: 0;
            overflow: hidden;
        }
        #gameCanvas {
            background-color: #f0f0f0;
            display: block;
        }
        #player {
            width: 50px;
            height: 50px;
            background-color: #ff0000;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
        }
    </style>
</head>
<body>
    <canvas id="gameCanvas"></canvas>
    <div id="player"></div>
    <script>
        const canvas = document.getElementById('gameCanvas');
        const player = document.getElementById('player');
        const ctx = canvas.getContext('2d');
        let playerX = window.innerWidth / 2;
        let playerY = window.innerHeight / 2;
        const playerSpeed = 5;

        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        function update() {
            player.style.left = playerX + 'px';
            player.style.top = playerY + 'px';
        }

        function gameLoop() {
            update();
            requestAnimationFrame(gameLoop);
        }

        window.addEventListener('keydown', (e) => {
            switch (e.key) {
                case 'ArrowUp':
                    playerY -= playerSpeed;
                    break;
                case 'ArrowDown':
                    playerY += playerSpeed;
                    break;
                case 'ArrowLeft':
                    playerX -= playerSpeed;
                    break;
                case 'ArrowRight':
                    playerX += playerSpeed;
                    break;
            }
        });

        gameLoop();
    </script>
</body>
</html>
