<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Final Pro Birthday Animation</title>

<!-- Google Fonts for stylish text -->
<link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Playfair+Display:wght@600&display=swap" rel="stylesheet">

<style>
/* -----------------------
   BODY & BACKGROUND
------------------------ */
body{
  margin:0;
  height:100vh;
  display:flex;
  justify-content:center;
  align-items:center;
  background:#b8e0d2; /* Soft single color */
  overflow:hidden;
}

/* -----------------------
   GLOW BEHIND CAKE
------------------------ */
.glow{
  position:absolute;
  width:460px;
  height:460px;
  background:radial-gradient(circle, rgba(255,255,255,0.6) 0%, transparent 70%);
  border-radius:50%;
  animation:glowPulse 3s ease-in-out infinite;
}
@keyframes glowPulse{
  0%,100%{transform:scale(1);}
  50%{transform:scale(1.08);}
}

/* -----------------------
   TEXT: HAPPY & BIRTHDAY
------------------------ */
.left-text, .right-text{
  position:absolute;
  opacity:0;
  z-index:100;
  animation:showText 1s forwards, popText 0.6s ease forwards;
  animation-delay:5s,5s;
}

/* "HAPPY" */
.left-text{
  left:5%;
  top:8%;
  font-family:'Playfair Display', serif;
  font-size:55px;
  letter-spacing:2px;
  background:linear-gradient(45deg,#ff6a88,#ff99ac,#ffd1dc);
  -webkit-background-clip:text;
  -webkit-text-fill-color:transparent;
  text-shadow:0 0 25px rgba(255,255,255,0.5);
}

/* "BIRTHDAY" */
.right-text{
  right:5%;
  top:8%;
  font-family:'Great Vibes', cursive;
  font-size:80px;
  background:linear-gradient(45deg,#ff4da6,#ff80bf,#ffc0cb);
  -webkit-background-clip:text;
  -webkit-text-fill-color:transparent;
  text-shadow:0 0 30px rgba(255,255,255,0.6);
}

@keyframes showText{to{opacity:1;}}
@keyframes popText{
  0%{transform:scale(0.5);}
  50%{transform:scale(1.15);}
  100%{transform:scale(1);}
}

/* -----------------------
   CAKE LAYERS
------------------------ */
.cake{
  position:relative;
  width:400px;
  height:300px;
  z-index:10;
}

.layer{
  position:absolute;
  border-radius:25px;
  opacity:0;
  left:50%;
  transform:translateX(-50%);
  box-shadow:0 15px 30px rgba(0,0,0,0.3);
}

/* Layer drop animations (from top) */
.layer1{width:360px;height:90px;background:#8e44ad;top:-200px;animation:drop1 1.5s forwards;}
.layer2{width:280px;height:80px;background:#f39c12;top:-200px;animation:drop2 1.5s forwards 1.5s;}
.layer3{width:200px;height:70px;background:#e74c3c;top:-200px;animation:drop3 1.5s forwards 3s;}

@keyframes drop1{to{top:200px;opacity:1;}}
@keyframes drop2{to{top:130px;opacity:1;}}
@keyframes drop3{to{top:70px;opacity:1;}}

/* -----------------------
   CANDLES
------------------------ */
.candle{
  position:absolute;
  width:14px;
  height:50px;
  background:white;
  top:20px;
  opacity:0;
  animation:showCandle 1s forwards 4.8s;
  border-radius:3px;
}

/* Individual candle positions */
.c1{left:150px;}
.c2{left:190px;}
.c3{left:230px;}

@keyframes showCandle{to{opacity:1;}}

/* -----------------------
   FLAMES
------------------------ */
.flame{
  width:14px;
  height:20px;
  background:gold;
  border-radius:50%;
  position:absolute;
  top:-20px;
  box-shadow:0 0 30px orange;
  animation:flicker 0.3s infinite alternate;
}
@keyframes flicker{
  from{transform:scale(1);}
  to{transform:scale(1.3);}
}

/* -----------------------
   FIREWORKS (CSS only)
------------------------ */
.firework{
  position:absolute;
  width:10px;
  height:10px;
  border-radius:50%;
  opacity:0;
  animation:fireBurst 1.8s cubic-bezier(.17,.67,.83,.67) infinite 5s;
}

/* Firework positions */
.fw-left{left:12%;top:15%;}
.fw-right{right:12%;top:15%;}

/* Firework burst particles */
.firework::before{
  content:"";
  position:absolute;
  width:10px;
  height:10px;
  border-radius:50%;
  box-shadow:
    0 -150px #ff004f,
    85px -110px #ff7f00,
    150px 0 #ffec00,
    85px 110px #32ff7e,
    0 150px #00d4ff,
    -85px 110px #ff00d4,
    -150px 0 #9b00ff,
    -85px -110px #ff3b3b,
    110px -40px #ffffff,
    -110px 40px #ffffff;
  animation:particles 1.6s ease-out infinite 5s;
}

@keyframes fireBurst{
  0%{opacity:1;transform:scale(0.2);}
  50%{opacity:1;transform:scale(1.6);}
  100%{opacity:0;transform:scale(2.2);}
}
@keyframes particles{
  0%{opacity:1;transform:scale(0.3);}
  100%{opacity:0;transform:scale(2.5);}
}

/* -----------------------
   CONFETTI
------------------------ */
.confetti{
  position:absolute;
  width:8px;
  height:8px;
  border-radius:50%;
  top:-10px;
  animation:confettiFall 6s linear infinite;
}
@keyframes confettiFall{
  0%{transform:translateY(0) rotate(0deg);}
  100%{transform:translateY(800px) rotate(360deg);}
}

</style>
</head>
<body>

<!-- GLOW BEHIND CAKE -->
<div class="glow"></div>

<!-- CAKE + LAYERS + CANDLES -->
<div class="cake">
  <div class="layer layer1"></div>
  <div class="layer layer2"></div>
  <div class="layer layer3"></div>

  <div class="candle c1"><div class="flame"></div></div>
  <div class="candle c2"><div class="flame"></div></div>
  <div class="candle c3"><div class="flame"></div></div>
</div>

<!-- HAPPY & BIRTHDAY TEXT -->
<div class="left-text">Happy</div>
<div class="right-text">Birthday</div>

<!-- FIREWORKS -->
<div class="firework fw-left"></div>
<div class="firework fw-right"></div>

<!-- CONFETTI -->
<div class="confetti" style="left:10%; background:#ff3b3b;"></div>
<div class="confetti" style="left:30%; background:#ffd700;"></div>
<div class="confetti" style="left:50%; background:#32ff7e;"></div>
<div class="confetti" style="left:70%; background:#ff00d4;"></div>
<div class="confetti" style="left:85%; background:#00d4ff;"></div>

</body>
</html>
