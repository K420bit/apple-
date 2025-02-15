# apple-<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>لعبة التفاحة</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="game-container">
        <canvas id="gameCanvas"></canvas>
        <button id="startGame">ابدأ اللعبة</button>
    </div>
    <script src="script.js"></script>
</body>
</html>body {
    text-align: center;
    background-color: #222;
    color: white;
    font-family: Arial, sans-serif;
}

.game-container {
    position: relative;
    margin: auto;
    width: 300px;
    height: 400px;
    background: #000;
    border: 2px solid #fff;
}

canvas {
    display: block;
    background-color: #444;
}const canvas = document.getElementById("gameCanvas");
const ctx = canvas.getContext("2d");
canvas.width = 300;
canvas.height = 400;

let apple = { x: 150, y: 50, radius: 10, dy: 2 };
let gameActive = false;

function drawApple() {
    ctx.fillStyle = "red";
    ctx.beginPath();
    ctx.arc(apple.x, apple.y, apple.radius, 0, Math.PI * 2);
    ctx.fill();
}

function updateGame() {
    if (!gameActive) return;
    
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    drawApple();
    apple.y += apple.dy;
    
    if (apple.y > canvas.height) {
        apple.y = 50;
    }
    
    requestAnimationFrame(updateGame);
}

document.getElementById("startGame").addEventListener("click", () => {
    gameActive = true;
    updateGame();
});
