<h1 align="center" style="color:#39FF14; text-shadow: 0 0 8px #39FF14, 0 0 20px #39FF14;">
  👾 Ro'zmamatov Kamolbek 👾
</h1>

<h3 align="center" style="color:#8A2BE2; text-shadow: 0 0 5px #8A2BE2, 0 0 10px #8A2BE2;">
  ⚡ Middle Frontend Developer | Code Gamer | UI Architect
</h3>

<p align="center">
  <a href="https://t.me/rkamolbekk99">
    <img src="https://img.shields.io/badge/Telegram-@rkamolbekk99-8A2BE2?style=for-the-badge&logo=telegram&logoColor=white"/>
  </a>
  <a href="https://k-ruzmamatov.netlify.app">
    <img src="https://img.shields.io/badge/Portfolio-Visit-39FF14?style=for-the-badge&logo=firefox&logoColor=black"/>
  </a>
  <a href="https://instagram.com/ruzmamatov.99">
    <img src="https://img.shields.io/badge/Instagram-@ruzmamatov.99-FF00FF?style=for-the-badge&logo=instagram&logoColor=white"/>
  </a>
</p>

---

# 🟡 Snake Game — Full Working Code

### 📄 index.html
```html
<!DOCTYPE html>
<html>
<head>
  <title>Snake Game</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <h1>Snake Game</h1>
  <canvas id="game" width="400" height="400"></canvas>
  <script src="script.js"></script>
</body>
</html>
```

### 🎨 style.css
```css
body {
  background: #0d1117;
  color: white;
  text-align: center;
  font-family: Arial;
}

canvas {
  background: black;
  border: 2px solid #00ff88;
}
```

### ⚙ script.js
```javascript
const canvas = document.getElementById("game");
const ctx = canvas.getContext("2d");

const box = 20;
const canvasSize = 400;

let snake = [{ x: 200, y: 200 }];
let direction = "RIGHT";

let food = {
  x: Math.floor(Math.random() * 20) * box,
  y: Math.floor(Math.random() * 20) * box
};

document.addEventListener("keydown", changeDirection);

function changeDirection(e) {
  if (e.key === "ArrowLeft" && direction !== "RIGHT") direction = "LEFT";
  if (e.key === "ArrowUp" && direction !== "DOWN") direction = "UP";
  if (e.key === "ArrowRight" && direction !== "LEFT") direction = "RIGHT";
  if (e.key === "ArrowDown" && direction !== "UP") direction = "DOWN";
}

function draw() {
  ctx.fillStyle = "black";
  ctx.fillRect(0, 0, canvasSize, canvasSize);

  for (let i = 0; i < snake.length; i++) {
    ctx.fillStyle = i === 0 ? "#00ff88" : "white";
    ctx.fillRect(snake[i].x, snake[i].y, box, box);
  }

  ctx.fillStyle = "red";
  ctx.fillRect(food.x, food.y, box, box);

  let headX = snake[0].x;
  let headY = snake[0].y;

  if (direction === "LEFT") headX -= box;
  if (direction === "UP") headY -= box;
  if (direction === "RIGHT") headX += box;
  if (direction === "DOWN") headY += box;

  if (
    headX < 0 || headY < 0 ||
    headX >= canvasSize || headY >= canvasSize ||
    collision(headX, headY, snake)
  ) {
    clearInterval(game);
    alert("Game Over");
  }

  if (headX === food.x && headY === food.y) {
    food = {
      x: Math.floor(Math.random() * 20) * box,
      y: Math.floor(Math.random() * 20) * box
    };
  } else {
    snake.pop();
  }

  const newHead = { x: headX, y: headY };
  snake.unshift(newHead);
}

function collision(x, y, array) {
  return array.some(segment => segment.x === x && segment.y === y);
}

const game = setInterval(draw, 100);
```

---

# 👾 Pacman Game — Full Working Code

### 📄 index.html
```html
<!DOCTYPE html>
<html>
<head>
  <title>Pacman</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <h1>Pacman</h1>
  <canvas id="game" width="400" height="400"></canvas>
  <script src="script.js"></script>
</body>
</html>
```

### 🎨 style.css
```css
body {
  background: #000;
  color: yellow;
  text-align: center;
}
canvas {
  background: #111;
  border: 2px solid yellow;
}
```

### ⚙ script.js
```javascript
const canvas = document.getElementById("game");
const ctx = canvas.getContext("2d");

let x = 200;
let y = 200;
let size = 20;

document.addEventListener("keydown", move);

function move(e) {
  if (e.key === "ArrowLeft") x -= size;
  if (e.key === "ArrowRight") x += size;
  if (e.key === "ArrowUp") y -= size;
  if (e.key === "ArrowDown") y += size;
}

function drawPacman() {
  ctx.fillStyle = "black";
  ctx.fillRect(0, 0, 400, 400);

  ctx.beginPath();
  ctx.arc(x, y, size, 0.2 * Math.PI, 1.8 * Math.PI);
  ctx.lineTo(x, y);
  ctx.fillStyle = "yellow";
  ctx.fill();
}

function gameLoop() {
  drawPacman();
  requestAnimationFrame(gameLoop);
}

gameLoop();
```

---
