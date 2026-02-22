<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Pacman Game</title>
<style>
    body {
        margin: 0;
        background: black;
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        font-family: Arial, sans-serif;
        color: white;
    }

    canvas {
        background: black;
        border: 4px solid yellow;
    }

    h1 {
        position: absolute;
        top: 20px;
        color: yellow;
    }
</style>
</head>
<body>

<h1>Pacman Game 👻</h1>
<canvas id="gameCanvas" width="600" height="600"></canvas>

<script>
const canvas = document.getElementById("gameCanvas");
const ctx = canvas.getContext("2d");

const tileSize = 30;
const rows = 20;
const cols = 20;

let pacman = {
    x: tileSize,
    y: tileSize,
    size: tileSize,
    dx: tileSize,
    dy: 0
};

let food = [];

for (let i = 0; i < rows; i++) {
    for (let j = 0; j < cols; j++) {
        food.push({ x: j * tileSize + tileSize/2, y: i * tileSize + tileSize/2 });
    }
}

function drawPacman() {
    ctx.beginPath();
    ctx.arc(pacman.x + tileSize/2, pacman.y + tileSize/2, tileSize/2, 0.2 * Math.PI, 1.8 * Math.PI);
    ctx.lineTo(pacman.x + tileSize/2, pacman.y + tileSize/2);
    ctx.fillStyle = "yellow";
    ctx.fill();
}

function drawFood() {
    ctx.fillStyle = "white";
    food.forEach((f, index) => {
        ctx.beginPath();
        ctx.arc(f.x, f.y, 4, 0, Math.PI * 2);
        ctx.fill();

        if (Math.abs(f.x - (pacman.x + tileSize/2)) < 10 &&
            Math.abs(f.y - (pacman.y + tileSize/2)) < 10) {
            food.splice(index, 1);
        }
    });
}

function update() {
    pacman.x += pacman.dx;
    pacman.y += pacman.dy;

    if (pacman.x < 0) pacman.x = canvas.width - tileSize;
    if (pacman.x >= canvas.width) pacman.x = 0;
    if (pacman.y < 0) pacman.y = canvas.height - tileSize;
    if (pacman.y >= canvas.height) pacman.y = 0;
}

function gameLoop() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    drawFood();
    drawPacman();
    update();
    requestAnimationFrame(gameLoop);
}

document.addEventListener("keydown", (e) => {
    switch(e.key) {
        case "ArrowUp":
            pacman.dx = 0;
            pacman.dy = -tileSize;
            break;
        case "ArrowDown":
            pacman.dx = 0;
            pacman.dy = tileSize;
            break;
        case "ArrowLeft":
            pacman.dx = -tileSize;
            pacman.dy = 0;
            break;
        case "ArrowRight":
            pacman.dx = tileSize;
            pacman.dy = 0;
            break;
    }
});

gameLoop();
</script>
<h1 align="center">👾 Ro'zmamatov Kamolbek 👾</h1>
<h3 align="center">⚡ Middle Frontend Developer | Code Gamer | UI Architect</h3>

<p align="center">
  <a href="https://t.me/rkamolbekk99">
    <img src="https://img.shields.io/badge/Telegram-@rkamolbekk99-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white"/>
  </a>
  <a href="https://k-ruzmamatov.netlify.app">
    <img src="https://img.shields.io/badge/Portfolio-Visit-000000?style=for-the-badge&logo=firefox&logoColor=white"/>
  </a>
</p>

---

# 🟡 Snake Game

<p align="center">
  <img src="https://raw.githubusercontent.com/platane/snk/output/github-contribution-grid-snake-dark.svg" />
</p>

---

## 🧠 About Me

```js
const kamolbek = {
  role: "Frontend Developer",
  level: "Middle",
  codeStyle: "Clean & Scalable",
  passion: ["Performance", "Modern UI", "Architecture"],
  openToWork: true
</body>
</html>

};
