<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Happiest Birthday Mahhh Piccchuuzilla! 🥳</title>
  <style>
    * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Poppins', cursive, sans-serif; }
    body { background: linear-gradient(135deg, #ffd1dc, #ffe6e8, #fff1f3); min-height: 100vh; display: flex; align-items: center; justify-content: center; overflow-x: hidden; text-align: center; color: #4a4a4a; }
    .card-container { width: 90%; max-width: 450px; background: rgba(255, 255, 255, 0.9); border-radius: 25px; padding: 25px; box-shadow: 0 15px 35px rgba(255, 182, 193, 0.4); position: relative; border: 2px solid #fff; }
    .page { display: none; animation: fadeIn 0.8s ease-in-out forwards; }
    .page.active { display: block; }
    @keyframes fadeIn { from { opacity: 0; transform: translateY(15px); } to { opacity: 1; transform: translateY(0); } }
    
    h1, h2 { color: #d63384; font-size: 1.5rem; margin-bottom: 15px; }
    p { font-size: 0.95rem; line-height: 1.6; color: #555; }
    
    .btn { background: linear-gradient(45deg, #ff758c, #ff7eb3); color: white; border: none; padding: 12px 25px; border-radius: 50px; font-size: 1rem; font-weight: bold; margin-top: 20px; cursor: pointer; box-shadow: 0 5px 15px rgba(255, 117, 140, 0.4); transition: 0.3s; }
    .btn:hover { transform: scale(1.05); }

    /* Interactive Cake */
    .cake-container { font-size: 80px; margin: 20px 0; cursor: pointer; }
    
    /* Letter Box */
    .letter-box { background: #fff5f7; border: 2px dashed #ffb6c1; border-radius: 15px; padding: 15px; text-align: left; font-size: 0.9rem; max-height: 250px; overflow-y: auto; margin: 15px 0; white-space: pre-line; }

    /* Video & Audio Player */
    .media-section { margin-top: 15px; }
    video { width: 100%; border-radius: 15px; border: 2px solid #ffb6c1; margin-top: 10px; }
    audio { width: 100%; margin-top: 10px; }

    /* Floating Flowers & Hearts */
    .floating-heart { position: fixed; font-size: 20px; animation: floatUp 4s linear infinite; bottom: -20px; z-index: 99; }
    @keyframes floatUp { 0% { transform: translateY(0) rotate(0deg); opacity: 1; } 100% { transform: translateY(-100vh) rotate(360deg); opacity: 0; } }
  </style>
</head>
<body>

  <!-- Background Music -->
  <audio id="bgMusic" loop>
    <source src="music.mp3" type="audio/mp3">
  </audio>

  <div class="card-container">
    
    <!-- PAGE 1: OPEN CARD -->
    <div class="page active" id="page1">
      <div style="font-size: 60px; margin-bottom: 15px;">💌</div>
      <h1>A Special Surprise for You!</h1>
      <p>Someone made something super cute for your birthday...</p>
      <button class="btn" onclick="nextPage(2)">Tap to Open 🎀</button>
    </div>

    <!-- PAGE 2: BLOW CANDLE -->
    <div class="page" id="page2">
      <h1>Make a Wish Queen! 🎂</h1>
      <p>Tap the cake to blow out the candle and make a wish 🕯️✨</p>
      <div class="cake-container" id="cake" onclick="blowCandle()">🎂</div>
      <p id="wishText" style="color: #ff758c; font-weight: bold;"></p>
      <button class="btn" id="next2Btn" style="display:none;" onclick="nextPage(3)">Read Your Letter 📜</button>
    </div>

    <!-- PAGE 3: LETTER & MEDIA -->
    <div class="page" id="page3">
      <h2>Happiest birthday mahhh piccchuuzilla 🥳🌸</h2>
      
      <div class="letter-box">
Mahhh Piccchuuuzillaaa 🥳❤️

Happiest birthday to my self-proclaimed queen 👑😭 I honestly don’t know how a random person I met ended up becoming such an important part of my everyday life haha. From annoying each other, teasing each other and having our stupid little fights to talking about literally random shit, I genuinely love all of it.

I hope this year brings u a really good college, a really good life and obviously enough patience to deal with me 😭. Keep being the same weird, annoying and funny person u are, and please don’t change too much hehe.

And finallyyy, welcome to 18, old lady 😈. Enjoy your day properly, queen. You deserve a really good one ❤️

— ur old man ♡
      </div>

      <!-- Video Player -->
      <div class="media-section">
        <p style="font-weight: bold; color: #d63384;">A Little Video For You 🎥</p>
        <video controls>
          <source src="video.mp4" type="video/mp4">
          Your browser does not support the video tag.
        </video>
      </div>

      <button class="btn" onclick="nextPage(4)">One Last Thing 💖</button>
    </div>

    <!-- PAGE 4: ENDING -->
    <div class="page" id="page4">
      <div style="font-size: 60px; margin-bottom: 15px;">🌸✨</div>
      <h1>Have the Best Day Ever! 🎉</h1>
      <p>Hope this brought a tiny smile to your face today. Stay blessed and keep shining bright!</p>
      <p style="margin-top: 15px; font-weight: bold; color: #ff758c;">Sending you lots of love & warm hugs! 🤗❤️</p>
    </div>

  </div>

  <script>
    function nextPage(pageNum) {
      document.querySelectorAll('.page').forEach(page => page.classList.remove('active'));
      document.getElementById('page' + pageNum).classList.add('active');
      
      // Play music on first tap
      let music = document.getElementById('bgMusic');
      if (music.paused) { music.play().catch(() => {}); }
    }

    function blowCandle() {
      document.getElementById('cake').innerHTML = '🍰✨';
      document.getElementById('wishText').innerText = 'Yay! May all your wishes come true! 🎉';
      document.getElementById('next2Btn').style.display = 'inline-block';
      spawnFlowers();
    }

    // Floating Hearts/Flowers
    function spawnFlowers() {
      const items = ['🌸', '🌺', '💖', '🎂', '✨', '💐'];
      for (let i = 0; i < 20; i++) {
        let heart = document.createElement('div');
        heart.className = 'floating-heart';
        heart.innerText = items[Math.floor(Math.random() * items.length)];
        heart.style.left = Math.random() * 100 + 'vw';
        heart.style.animationDuration = (Math.random() * 2 + 3) + 's';
        document.body.appendChild(heart);
      }
    }
    setInterval(spawnFlowers, 3000);
  </script>
</body>
</html>
