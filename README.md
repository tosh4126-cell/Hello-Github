<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>❤️</title>

<style>
* {margin:0;padding:0;box-sizing:border-box}

body {
  height:100vh;
  overflow:hidden;
  background:radial-gradient(circle,#350015,#100008 65%,#020003);
}

.stars {
  position:fixed;
  inset:0;
  background-image:radial-gradient(#fff 1px,transparent 1px);
  background-size:45px 45px;
  opacity:.3;
}

.heart-svg {
  position:fixed;
  width:95vmin;
  height:95vmin;
  top:50%;
  left:50%;
  transform:translate(-50%,-50%);
  overflow:visible;
}

.heart {
  fill:transparent;
  stroke:#ff174f;
  stroke-width:3;
  stroke-linecap:round;
  stroke-dasharray:1000;
  stroke-dashoffset:1000;
  filter:drop-shadow(0 0 12px #ff174f)
         drop-shadow(0 0 30px #ff174f);
  animation:draw 5s ease forwards,beat 1.2s 5s infinite;
  transform-box:fill-box;
  transform-origin:center;
}

@keyframes draw {
  to {stroke-dashoffset:0}
}

@keyframes beat {
  0%,100% {transform:scale(1)}
  15% {transform:scale(1.04)}
  30% {transform:scale(1)}
  45% {transform:scale(1.03)}
}

button {
  position:fixed;
  bottom:8%;
  left:50%;
  transform:translateX(-50%);
  padding:15px 32px;
  border:1px solid #ff799d;
  border-radius:40px;
  background:#a9003c;
  color:white;
  font-size:14px;
  letter-spacing:2px;
  box-shadow:0 0 20px #ff174f;
  cursor:pointer;
  z-index:5;
}

.particle {
  position:fixed;
  bottom:-30px;
  color:#ff739c;
  animation:rise 8s linear forwards;
  pointer-events:none;
}

@keyframes rise {
  to {transform:translateY(-110vh) rotate(360deg);opacity:0}
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

<button onclick="toggleMusic()" id="btn">
♫ PLAY OUR SONG
</button>

<audio id="song" src="song.mp3" loop></audio>

<script>
const song=document.getElementById("song");
const btn=document.getElementById("btn");

function toggleMusic(){
  if(song.paused){
    song.play().then(()=>{
      btn.innerHTML="Ⅱ PAUSE SONG";
    }).catch(()=>{
      alert("Please upload song.mp3");
    });
  }else{
    song.pause();
    btn.innerHTML="♫ PLAY OUR SONG";
  }
}

setInterval(()=>{
  const p=document.createElement("div");
  p.className="particle";
  p.innerHTML=Math.random()>.5?"♥":"✦";
  p.style.left=Math.random()*100+"vw";
  p.style.fontSize=(15+Math.random()*20)+"px";
  document.body.appendChild(p);
  setTimeout(()=>p.remove(),8000);
},450);
</script>

</body>
</html>
