<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>For Yasser ❤️</title>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  width: 100%;
  height: 100vh;
  overflow: hidden;
  background: radial-gradient(circle at center,
    #350015, #12000a 65%, #030003);
  color: white;
  font-family: Georgia, serif;
}

.stars {
  position: fixed;
  inset: 0;
  background-image: radial-gradient(#fff 1px, transparent 1px);
  background-size: 45px 45px;
  opacity: .3;
}

.heart-svg {
  position: fixed;
  width: min(100vw, 100vh);
  height: min(100vw, 100vh);
  max-width: 100vw;
  max-height: 100vh;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -53%);
  overflow: visible;
  z-index: 1;
}

.heart {
  fill: transparent;
  stroke: #ff174f;
  stroke-width: 3;
  stroke-linecap: round;
  stroke-linejoin: round;
  stroke-dasharray: 1000;
  stroke-dashoffset: 1000;
  filter: drop-shadow(0 0 10px #ff174f)
          drop-shadow(0 0 25px #ff174f);
  animation:
    draw 5s ease-in-out forwards,
    beat 1.2s 5s infinite;
  transform-box: fill-box;
  transform-origin: center;
}

@keyframes draw {
  to { stroke-dashoffset: 0; }
}

@keyframes beat {
  0%,100% { transform: scale(1); }
  15% { transform: scale(1.04); }
  30% { transform: scale(1); }
  45% { transform: scale(1.03); }
}

.content {
  position: relative;
  z-index: 3;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  pointer-events: none;
}

.top {
  position: absolute;
  top: 8%;
  color: #ff9db8;
  font-size: 12px;
  letter-spacing: 7px;
}

.name {
  margin-top: 45vh;
  font-size: clamp(30px, 8vw, 48px);
  letter-spacing: 10px;
  font-weight: bold;
  color: white;
  text-shadow: 0 0 15px #ff174f, 0 0 35px #ff174f;
  animation: appear 3s 4.5s both;
}

.message {
  margin-top: 15px;
  font-size: 21px;
  color: #ffb1c8;
  font-style: italic;
  animation: appear 3s 5s both;
}

button {
  pointer-events: auto;
  position: absolute;
  bottom: 7%;
  padding: 14px 30px;
  border-radius: 35px;
  border: 1px solid #ff799d;
  background: #a9003c;
  color: white;
  font-size: 14px;
  letter-spacing: 2px;
  box-shadow: 0 0 20px #ff174f;
  cursor: pointer;
}

@keyframes appear {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

.particle {
  position: fixed;
  bottom: -30px;
  color: #ff739c;
  z-index: 2;
  animation: rise 8s linear forwards;
  pointer-events: none;
}

@keyframes rise {
  to {
    transform: translateY(-110vh) rotate(360deg);
    opacity: 0;
  }
}
</style>
</head>

<body>

<div class="stars"></div>

<svg class="heart-svg" viewBox="0 0 400 360">
  <path class="heart"
    pathLength="1000"
    d="M200 340
       C165 305 15 200 15 105
       C15 15 130 -10 200 90
       C270 -10 385 15 385 105
       C385 200 235 305 200 340 Z"/>
</svg>

<div class="content">
  <div class="top">A LITTLE MESSAGE FOR YOU</div>

  <div class="name">YASSER</div>

  <div class="message">I Wanna Be Yours ❤️</div>

  <button onclick="toggleMusic()" id="musicBtn">
    ♫ PLAY OUR SONG
  </button>
</div>

<audio id="song" src="song.mp3" loop></audio>

<script>
const song = document.getElementById("song");
const btn = document.getElementById("musicBtn");

function toggleMusic() {
  if (song.paused) {
    song.play().then(() => {
      btn.innerHTML = "Ⅱ PAUSE SONG";
    }).catch(() => {
      alert("Please upload song.mp3 to your repository.");
    });
  } else {
    song.pause();
    btn.innerHTML = "♫ PLAY OUR SONG";
  }
}

setInterval(() => {
  const p = document.createElement("div");
  p.className = "particle";
  p.innerHTML = Math.random() > .5 ? "♥" : "✦";
  p.style.left = Math.random() * 100 + "vw";
  p.style.fontSize = (15 + Math.random()*20) + "px";
  document.body.appendChild(p);
  setTimeout(() => p.remove(), 8000);
}, 450);
</script>

</body>
</html>
