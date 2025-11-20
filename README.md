<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>🌌 Space Hub 🌌</title>

<style>
@import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@500&display=swap');

body {
    margin:0;
    font-family:'Orbitron', sans-serif;
    background:black;
    overflow:hidden;
    color:#0ff;
    text-align:center;
}

/* ---------------- STARFIELD ANIMATION ---------------- */
.star {
    position:absolute;
    background:white;
    border-radius:50%;
    opacity:0.8;
    animation: drift linear forwards;
}
@keyframes drift {
    from { transform:translateY(-10px); }
    to { transform:translateY(110vh); }
}

/* ---------------- HOLOGRAM PANEL ---------------- */
.holoPanel {
    width: 70%;
    margin: 0 auto;
    margin-top: 40px;
    padding: 20px;
    border: 2px solid #0ff;
    border-radius: 10px;
    background: rgba(0, 20, 40, 0.55);
    backdrop-filter: blur(6px);
    box-shadow: 0 0 25px #0ff, inset 0 0 25px #0ff;
}

/* ---------------- BUTTONS / LINKS ---------------- */
button, .gameLink {
    padding: 12px 25px;
    margin: 8px;
    font-size: 18px;
    cursor:pointer;
    background: linear-gradient(45deg, #00faff, #00b8ff);
    color:black;
    border:none;
    border-radius:5px;
    box-shadow:0 0 25px #0ff;
    transition:0.3s ease;
    text-decoration: none;
    display: inline-block;
    font-weight: bold;
}

button:hover, .gameLink:hover {
    box-shadow:0 0 45px #0ff, 0 0 10px #0ff inset;
    transform:scale(1.08);
}

h1 {
    margin-top: 20px;
    text-shadow:0 0 15px #0ff, 0 0 30px #0ff;
}

.screen {
    padding:20px;
}

#gamesContainer {
    margin-top:20px;
}

/* ---------------- COINS DISPLAY ---------------- */
#coinsDisplay {
    color: #f8ff44;
    text-shadow: 0 0 10px #faff72;
    font-weight: bold;
    font-size: 22px;
}
</style>
</head>
<body>

<h1>🌌 Space Hub 🌌</h1>

<!-- MAIN HOLOGRAM PANEL -->
<div id="lobbyScreen" class="holoPanel screen">
    <h2>Welcome, Pilot!</h2>
    <p>Your Credits: <span id="coinsDisplay">0</span></p>

    <div id="gamesContainer">
        <a class="gameLink" href="Space Game.html">🚀 Launch Space Game</a>
        <a class="gameLink" href="Space Defender.html">🛡 Deploy to Space Defender</a>
    </div>
</div>

<script>
/* ===============================
    STARFIELD BACKGROUND
================================*/
function createStar(){
    const star = document.createElement("div");
    star.classList.add("star");

    const size = Math.random() * 3 + 1;
    star.style.width = size + "px";
    star.style.height = size + "px";
    star.style.left = Math.random() * 100 + "vw";
    star.style.top = "-10px";
    star.style.animationDuration = (Math.random()*5 + 5) + "s";

    document.body.appendChild(star);

    setTimeout(()=> star.remove(), 11000);
}
setInterval(createStar, 80);

/* ===============================
      PLAYER STORAGE SYSTEM
================================*/
let players = JSON.parse(localStorage.getItem("players")||"{}");
let currentPlayer = "Pilot";

if (!players[currentPlayer]) {
    players[currentPlayer] = { coins: 0 };
    localStorage.setItem("players", JSON.stringify(players));
}

document.getElementById("coinsDisplay").textContent = players[currentPlayer].coins;
</script>

</body>
</html>
