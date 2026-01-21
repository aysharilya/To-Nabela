<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Happy Birthday Nabela</title>

<script src="https://cdn.tailwindcss.com"></script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Quicksand:wght@400;600&display=swap');

body{
    font-family:'Quicksand',sans-serif;
    background:linear-gradient(135deg,#ffe4e1,#ffc0cb);
    overflow:hidden;
    color:#d81b60;
}

/* ===== KUE 3D ===== */
.cake-container{
    cursor:pointer;
    transform:perspective(900px) rotateX(15deg);
    transition:transform .4s ease;
}
.cake-container:hover{
    transform:perspective(900px) rotateX(0deg) scale(1.07);
}

/* Lilin */
.flame{
    width:14px;
    height:22px;
    background:#ffdb58;
    border-radius:50% 50% 35% 35%;
    position:absolute;
    top:-22px;
    left:50%;
    transform:translateX(-50%);
    animation:flicker .1s infinite;
    box-shadow:0 0 10px #ffdb58;
}
@keyframes flicker{
    0%{transform:translateX(-50%) scale(1);}
    50%{transform:translateX(-50%) scale(1.1);}
    100%{transform:translateX(-50%) scale(1);}
}

/* ===== ORNAMEN ===== */
.balloon{
    position:absolute;
    width:50px;
    height:70px;
    border-radius:50%;
    bottom:-100px;
    opacity:.8;
    animation:float 6s linear infinite;
}
@keyframes float{
    from{transform:translateY(0)}
    to{transform:translateY(-120vh)}
}

.confetti{
    position:absolute;
    width:10px;
    height:10px;
    animation:confetti 3s linear infinite;
}
@keyframes confetti{
    from{transform:translateY(-10vh) rotate(0deg)}
    to{transform:translateY(110vh) rotate(360deg)}
}

.star{
    position:absolute;
    font-size:20px;
    animation:sparkle 3s infinite;
}
@keyframes sparkle{
    0%{opacity:0;transform:scale(0)}
    50%{opacity:1;transform:scale(1.3)}
    100%{opacity:0;transform:scale(0)}
}

.hidden{display:none}
.font-birthday{font-family:'Dancing Script',cursive}
</style>
</head>

<body class="h-screen flex items-center justify-center relative">

<div id="ornaments"></div>

<!-- PAGE 1 -->
<div id="page1" class="z-10 text-center">
<h1 class="text-6xl font-birthday mb-10 animate-bounce drop-shadow-lg">
Happy Birthday Nabela 🎉
</h1>

<div class="cake-container relative mx-auto" onclick="blowCandle()">

<!-- KUE ATAS -->
<div class="w-48 h-32 bg-pink-300 rounded-t-xl border-b-8 border-pink-400 shadow-2xl relative">
<div class="absolute -bottom-3 flex w-full justify-around">
<div class="w-8 h-8 bg-pink-300 rounded-full"></div>
<div class="w-8 h-8 bg-pink-300 rounded-full"></div>
<div class="w-8 h-8 bg-pink-300 rounded-full"></div>
</div>

<!-- LILIN -->
<div class="w-3 h-12 bg-white absolute -top-12 left-1/2 -translate-x-1/2 rounded-full">
<div id="flame" class="flame"></div>
</div>
</div>

<!-- KUE BAWAH (BIAR 3D) -->
<div class="w-48 h-6 bg-pink-400 rounded-b-xl shadow-lg"></div>
<div class="w-56 h-4 bg-white rounded-full mt-2 shadow-md"></div>
</div>

<p class="mt-10 italic animate-pulse">
Klik lilinnya ya 🎂
</p>
</div>

<!-- PAGE 2 -->
<div id="page2" class="hidden z-10 text-center px-6">
<div class="bg-white/80 p-10 rounded-3xl shadow-2xl">
<h2 class="text-4xl font-birthday mb-6">Barakallah Fii Umrik ✨</h2>
<p class="text-lg">
Semoga sehat, bahagia, dan semua mimpi lo satu-satu check list ✔️
</p>
<button onclick="location.reload()" class="mt-8 bg-pink-500 text-white px-6 py-2 rounded-full hover:bg-pink-600">
Ulang Lagi 🎁
</button>
</div>
</div>

<!-- AUDIO -->
<audio id="bgMusic" loop>
<source src="happy-birthday-254480.mp3" type="audio/mpeg">
</audio>

<script>
const ornaments=document.getElementById('ornaments');
const colors=['#ff69b4','#ffc0cb','#ffffff','#da70d6'];

function balloon(){
const b=document.createElement('div');
b.className='balloon';
b.style.left=Math.random()*100+'vw';
b.style.background=colors[Math.floor(Math.random()*colors.length)];
ornaments.appendChild(b);
setTimeout(()=>b.remove(),6000);
}

function confetti(){
const c=document.createElement('div');
c.className='confetti';
c.style.left=Math.random()*100+'vw';
c.style.background=colors[Math.floor(Math.random()*colors.length)];
ornaments.appendChild(c);
setTimeout(()=>c.remove(),3000);
}

function star(){
const s=document.createElement('div');
s.className='star';
s.innerHTML='✨';
s.style.left=Math.random()*100+'vw';
s.style.top=Math.random()*100+'vh';
ornaments.appendChild(s);
setTimeout(()=>s.remove(),3000);
}

setInterval(balloon,500);
setInterval(star,400);

function blowCandle(){
document.getElementById('flame').style.display='none';
document.getElementById('bgMusic').play();
setTimeout(()=>{
page1.classList.add('hidden');
page2.classList.remove('hidden');
setInterval(confetti,100);
},700);
}
</script>

</body>
</html>
