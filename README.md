<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<title>🩷</title>

<style>
body {
  margin: 0;
  height: 100vh;
  background: linear-gradient(135deg, #ff69b4, #ffc0cb);
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: Arial, sans-serif;
  overflow: hidden;
}

/* Фон сердечек */
.hearts-bg {
  position: fixed;
  width: 100%;
  height: 100%;
  pointer-events: none;
  background-image: url("https://pngimg.com/uploads/heart/heart_PNG51335.png");
  background-size: 40px;
  opacity: 0.18;
}

/* Падающие сердечки */
.falling-heart {
  position: fixed;
  top: -50px;
  font-size: 24px;
  animation: fall linear forwards;
  color: #ff1493;
}

@keyframes fall {
  to {
    transform: translateY(110vh);
    opacity: 0;
  }
}

/* Карточка */
.card {
  background: rgba(255, 105, 180, 0.9);
  padding: 30px;
  border-radius: 30px;
  max-width: 360px;
  text-align: center;
  color: white;
  z-index: 2;
}

img {
  width: 100%;
  border-radius: 20px;
  margin-bottom: 15px;
}

.buttons {
  margin-top: 20px;
  position: relative;
  height: 80px;
}

/* Кнопки */
button {
  padding: 12px 28px;
  font-size: 18px;
  border: none;
  border-radius: 30px;
  cursor: pointer;
}

#yes {
  background: #ff1493;
  color: white;
}

/* ДРОЖАЩИЙ НЕТ */
#no {
  background: #ff69b4;
  color: white;
  position: absolute;
  animation: shake 0.4s infinite;
}

@keyframes shake {
  0% { transform: translate(0,0); }
  25% { transform: translate(2px,0); }
  50% { transform: translate(-2px,0); }
  75% { transform: translate(2px,0); }
  100% { transform: translate(0,0); }
}
</style>
</head>

<body>

<div class="hearts-bg"></div>

<!-- МУЗЫКА -->
<audio id="music" loop>
  <source src="https://files.freemusicarchive.org/storage-freemusicarchive-org/music/no_curator/Kevin_MacLeod/Classical_Sampler/Kevin_MacLeod_-_Carefree.mp3">
</audio>

<div class="card" id="main">
  <!-- КОТИК С СЕРДЕЧКАМИ -->
  <img src="https://media.giphy.com/media/JIX9t2j0ZTN9S/giphy.gif" alt="cute cat">

  <h2>Гүлжаухар, будешь моей валентинкой 🩷</h2>

  <div class="buttons">
    <button id="yes" onclick="yes()">ДА</button>
    <button id="no" onmouseover="moveNo()">НЕТ</button>
  </div>
</div>

<script>
function moveNo() {
  const no = document.getElementById("no");
  const x = Math.random() * (window.innerWidth - 120);
  const y = Math.random() * (window.innerHeight - 120);
  no.style.left = x + "px";
  no.style.top = y + "px";
}

function createHeart() {
  const heart = document.createElement("div");
  heart.className = "falling-heart";
  heart.innerText = "🩷";
  heart.style.left = Math.random() * 100 + "vw";
  heart.style.animationDuration = (2 + Math.random() * 3) + "s";
  document.body.appendChild(heart);
  setTimeout(() => heart.remove(), 5000);
}

function yes() {
  document.getElementById("music").play();

  setInterval(createHeart, 200);

  document.body.innerHTML = `
    <div class="hearts-bg"></div>
    <div class="card">
      <img src="https://media.giphy.com/media/MDJ9IbxxvDUQM/giphy.gif" alt="love cat">
      <h1>УРААААААААА!!! 🩷🩷🩷</h1>
      <p>
        Я ТАК РАД 🩷🩷🩷🩷🩷<br><br>
        Место встречи и время напишу,<br>
        с любовью Бағдаулет 🩷🩷🩷
      </p>
    </div>
  `;
}
</script>

</body>
</html>
