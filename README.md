<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>For You ❤️</title>
<link href="https://fonts.googleapis.com/css2?family=Great+Vibes&display=swap" rel="stylesheet">
<style>
body{
margin:0;
font-family:Arial;
background:linear-gradient(135deg,#6b0036,#b30059);
color:white;
text-align:center;
min-height:100vh;       /* allow body to grow */
overflow-x:hidden;       /* prevent horizontal scroll */
padding-top:50px;        /* space at top */
transition:background 3s;
}

/* MAIN BOX */
.container{
z-index:2;
animation:fadeIn 2s;
max-width:90%;
margin:0 auto;
}

/* BUTTON */
button{
padding:12px 25px;
border:none;
border-radius:20px;
background:white;
color:#b30059;
font-size:18px;
cursor:pointer;
}

/* AVATAR */
.avatar{
font-size:80px;
opacity:0;
transform:translateY(50px);
transition:1s;
}

/* FLOWER HANDOVER */
.gift{
font-size:120px;
opacity:0;
transform:scale(0.5);
transition:1s;
}

/* SHOW ANIMATION */
.show{
opacity:1;
transform:scale(1.1) translateY(0);
}
.avatar, .gift{
position:sticky;
top:20px;
z-index:2;
}
/* TYPING TEXT */
.message{
margin-top:20px;
font-size:32px;
min-height:100px;
font-family:'Great Vibes', cursive;
letter-spacing:2px;
line-height:1.6;
text-shadow:0 0 10px rgba(255,255,255,0.8);
color:#fff;
}

/* HEARTS */
.heart{
position:absolute;
font-size:24px;
animation:floatUp 3s forwards;
}

/* FLOWER RAIN */
.flower{
position:absolute;
top:-50px;
font-size:24px;
animation:fall linear infinite;
}

@keyframes fall{
to{transform:translateY(110vh);}
}

@keyframes floatUp{
0%{opacity:1;transform:translateY(0);}
100%{opacity:0;transform:translateY(-200px);}
}

@keyframes fadeIn{
from{opacity:0;}
to{opacity:1;}
}

/* FINAL HEART SURPRISE */
#finalHeart{
font-size:80px;
opacity:0;
transition:1s;
text-shadow:0 0 20px rgba(255,0,150,0.9);
}
.showHeart{
opacity:1;
transform:scale(1.2);
}
</style>
</head>

<body>

<audio id="music" loop>
<source src="perfect.mp3" type="audio/mpeg">
</audio>


<div class="container">

<h1>Hey ❤️</h1>
<p>I made something just for you…</p>

<button onclick="startMagic()">Open Your Gift 💐</button>

<div id="avatar" class="avatar">😊</div>
<div id="gift" class="gift">💐</div>

<div id="text" class="message"></div>

<div id="finalHeart">💖</div>

</div>

<script>
/* ✍️ PERSONAL MESSAGE */
const loveMessage = `
happy birthday my lady, i wish u a long life with all the good it has to offer you, you are such an amazing person, meeting you was the best think to happen to me, in this day i want you to know that i am lucky to have you, lucky to have had all those beautiful moments with you, all the laughter we had, the tears i wiped off your cheeks, the stories nd the experiences we lived together, i will never forget those, i will never forget you, you will forever be a part of me that i won't let go, i want you to be happy sweetie, to live you life to the fullest, u have a lot of beautiful things ahead, embrace them with a smile. you also have a lot of achivements to do, i'm sure you will do all that, with that beautiful heart of yours, nd that magical smile, nd brilliant mind, you will do a lot indeed. happy birthday again, i like you soo much sweetheart, take care of yourself. "
`;

/* CLICK ACTION */
function startMagic(){
const music = document.getElementById("music");
music.volume = 0.4;   // softer romantic volume
music.play().catch(()=>{});

/* avatar appears */
const avatar=document.getElementById("avatar");
avatar.classList.add("show");

/* after 1s → give flowers */
setTimeout(()=>{
document.getElementById("gift").classList.add("show");
createHearts();
typeText();
changeBackground();
},1000);
}

/* TYPING EFFECT */
function typeText(){
let i=0;
const speed=45;
const textBox=document.getElementById("text");

function typing(){
if(i<loveMessage.length){
textBox.innerHTML+=loveMessage.charAt(i);
i++;
setTimeout(typing,speed);
}else{
showFinalHeart();
}
}
typing();
}

/* HEARTS */
function createHearts(){
for(let i=0;i<35;i++){
const heart=document.createElement("div");
heart.className="heart";
heart.innerHTML=["💗","💖","💘"][Math.floor(Math.random()*3)];
heart.style.left=Math.random()*100+"vw";
heart.style.top=Math.random()*100+"vh";
document.body.appendChild(heart);
setTimeout(()=>heart.remove(),3000);
}
}

/* FLOWER RAIN */
function createFlower(){
const flowers=["🌸","🌹","🌷","🪻"];
const flower=document.createElement("div");
flower.className="flower";
flower.innerHTML=flowers[Math.floor(Math.random()*flowers.length)];
flower.style.left=Math.random()*100+"vw";
flower.style.animationDuration=(Math.random()*5+5)+"s";
document.body.appendChild(flower);
setTimeout(()=>flower.remove(),10000);
}

setInterval(createFlower,400);

/* NIGHT SKY BACKGROUND */
function changeBackground(){
document.body.style.background = "linear-gradient(135deg,#120022,#3d003f)";
}

/* FINAL HEART SURPRISE */
function showFinalHeart(){
const heart=document.getElementById("finalHeart");
heart.classList.add("showHeart");
}
</script>

</body>
</html
