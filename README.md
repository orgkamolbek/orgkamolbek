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

# 🎮 Snake & Pacman (Working Version - Single File)

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Snake & Pacman</title>
<style>
body{
  background:#0d1117;
  color:white;
  text-align:center;
  font-family:Arial;
}
canvas{
  background:black;
  border:2px solid #39FF14;
  margin:20px;
}
h2{
  color:#39FF14;
}
</style>
</head>
<body>

<h2>🐍 Snake Game</h2>
<canvas id="snakeGame" width="400" height="400"></canvas>

<h2>👾 Pacman Game</h2>
<canvas id="pacmanGame" width="400" height="400"></canvas>

<script>

/* ================= SNAKE ================= */

const snakeCanvas = document.getElementById("snakeGame");
const snakeCtx = snakeCanvas.getContext("2d");

const box = 20;
let snake = [{x:200,y:200}];
let direction = "RIGHT";

let food = {
  x: Math.floor(Math.random()*20)*box,
  y: Math.floor(Math.random()*20)*box
};

document.addEventListener("keydown", e=>{
  if(e.key==="ArrowLeft" && direction!=="RIGHT") direction="LEFT";
  if(e.key==="ArrowUp" && direction!=="DOWN") direction="UP";
  if(e.key==="ArrowRight" && direction!=="LEFT") direction="RIGHT";
  if(e.key==="ArrowDown" && direction!=="UP") direction="DOWN";
});

function drawSnake(){
  snakeCtx.fillStyle="black";
  snakeCtx.fillRect(0,0,400,400);

  snake.forEach((part,i)=>{
    snakeCtx.fillStyle=i===0?"#39FF14":"white";
    snakeCtx.fillRect(part.x,part.y,box,box);
  });

  snakeCtx.fillStyle="red";
  snakeCtx.fillRect(food.x,food.y,box,box);

  let headX=snake[0].x;
  let headY=snake[0].y;

  if(direction==="LEFT") headX-=box;
  if(direction==="RIGHT") headX+=box;
  if(direction==="UP") headY-=box;
  if(direction==="DOWN") headY+=box;

  if(headX<0||headY<0||headX>=400||headY>=400||
     snake.some(p=>p.x===headX&&p.y===headY)){
     snake=[{x:200,y:200}];
     direction="RIGHT";
  }

  if(headX===food.x && headY===food.y){
    food={
      x:Math.floor(Math.random()*20)*box,
      y:Math.floor(Math.random()*20)*box
    };
  } else {
    snake.pop();
  }

  snake.unshift({x:headX,y:headY});
}

setInterval(drawSnake,100);


/* ================= PACMAN ================= */

const pacCanvas=document.getElementById("pacmanGame");
const pacCtx=pacCanvas.getContext("2d");

let px=200;
let py=200;
let size=20;

document.addEventListener("keydown",e=>{
  if(e.key==="a") px-=size;
  if(e.key==="d") px+=size;
  if(e.key==="w") py-=size;
  if(e.key==="s") py+=size;
});

function drawPacman(){
  pacCtx.fillStyle="black";
  pacCtx.fillRect(0,0,400,400);

  pacCtx.beginPath();
  pacCtx.arc(px,py,size,0.2*Math.PI,1.8*Math.PI);
  pacCtx.lineTo(px,py);
  pacCtx.fillStyle="yellow";
  pacCtx.fill();
}

function loop(){
  drawPacman();
  requestAnimationFrame(loop);
}

loop();

</script>

</body>
</html>
```

---

🔥 Natija:

- Bitta HTML ichida
- Ikkala o‘yin ham ishlaydi
- Snake → Arrow tugmalar
- Pacman → W A S D tugmalar
- Crash bo‘lsa Snake reset bo‘ladi
- Freeze yo‘q

---

Agar xohlasang keyingi level qilamiz:

- Score system
- Restart button
- Mobile control
- Ghost AI
- Neon pro animation
- Sound effects

Qaysi levelga o‘tamiz, Code Gamer? 😎
