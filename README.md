<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Will You Be My Valentine?</title>
  <style>
    body {
      font-family: 'Arial', sans-serif;
      background-color: #ffebee;
      text-align: center;
      padding: 50px;
      margin: 0;
      overflow: hidden;
      position: relative;
    }
    h1 {
      color: #d32f2f;
      font-size: 3em;
      animation: fadeIn 2s ease-in-out;
    }
    p {
      color: #c62828;
      font-size: 1.5em;
      animation: fadeIn 3s ease-in-out;
    }
    button {
      background-color: #d32f2f;
      color: white;
      border: none;
      padding: 15px 30px;
      font-size: 1.2em;
      cursor: pointer;
      border-radius: 10px;
      animation: pulse 2s infinite, glow 1.5s infinite alternate;
      transition: transform 0.3s ease;
    }
    button:hover {
      background-color: #b71c1c;
      transform: scale(1.1);
    }
    .hidden {
      display: none;
    }
    .heart {
      color: #d32f2f;
      font-size: 2em;
      animation: float 3s ease-in-out infinite;
    }
    .image-container {
      margin: 20px auto;
      width: 300px;
      height: 300px;
      border-radius: 20px;
      overflow: hidden;
      box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
      animation: zoomIn 2s ease-in-out;
    }
    .image-container img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      transition: transform 0.5s ease;
    }
    @keyframes fadeIn {
      from { opacity: 0; }
      to { opacity: 1; }
    }
    @keyframes pulse {
      0% { transform: scale(1); }
      50% { transform: scale(1.1); }
      100% { transform: scale(1); }
    }
    @keyframes glow {
      0% { box-shadow: 0 0 10px #d32f2f; }
      100% { box-shadow: 0 0 20px #d32f2f; }
    }
    @keyframes float {
      0% { transform: translateY(0); }
      50% { transform: translateY(-10px); }
      100% { transform: translateY(0); }
    }
    @keyframes zoomIn {
      from { transform: scale(0.8); opacity: 0; }
      to { transform: scale(1); opacity: 1; }
    }
    .hearts {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      overflow: hidden;
      pointer-events: none;
    }
    .hearts span {
      position: absolute;
      color: #d32f2f;
      font-size: 2em;
      animation: fall 5s linear infinite;
    }
    @keyframes fall {
      0% { top: -10%; transform: translateX(0) rotate(0deg); }
      100% { top: 110%; transform: translateX(200px) rotate(360deg); }
    }
    .flower {
      position: absolute;
      font-size: 2em;
      animation: flower-fall 5s linear infinite;
    }
    @keyframes flower-fall {
      0% { top: -10%; transform: translateX(0) rotate(0deg); }
      100% { top: 110%; transform: translateX(200px) rotate(360deg); }
    }
  </style>
</head>
<body>
  <!-- Falling Hearts -->
  <div class="hearts">
    <span style="left: 10%; animation-delay: 0s;">❤️</span>
    <span style="left: 20%; animation-delay: 1s;">❤️</span>
    <span style="left: 30%; animation-delay: 2s;">❤️</span>
    <span style="left: 40%; animation-delay: 3s;">❤️</span>
    <span style="left: 50%; animation-delay: 4s;">❤️</span>
    <span style="left: 60%; animation-delay: 5s;">❤️</span>
    <span style="left: 70%; animation-delay: 6s;">❤️</span>
    <span style="left: 80%; animation-delay: 7s;">❤️</span>
    <span style="left: 90%; animation-delay: 8s;">❤️</span>
  </div>
  <audio id="background-music" autoplay loop>
    <source src="music.mp3" type="audio/mpeg">
  </audio> 
  <!-- Main Content -->
  <h1>Will You Be My Valentine?</h1>
  <p>Hey love, I have a very important question for you...</p>

  <!-- Image Container -->
  <div class="image-container">
    <img id="valentine-image" src="./IMG_8911.JPG" alt="Romantic GIF">
  </div>
  <div class="button-container">
    <button id="yes-btn" class="valentine-btn" onclick="showResponse()">Yes</button>
    <button id="no-btn" class="valentine-btn" onclick="resizeButtons()">No</button>
  </div>
  <div id="response" class="hidden">
    <p class="heart">❤️</p>
    <p>Thank you for making me the happiest person! 我爱你宝贝儿 💕</p>
  </div>

  <!-- Flower Container -->
  <div id="flower-container" class="hidden"></div> 
  <script>
    // Function to show the response and trigger animations
    function showResponse() {
      document.getElementById('response').classList.remove('hidden');
      document.getElementById('yes-btn').classList.add('hidden');
      document.getElementById('no-btn').classList.add('hidden');
      const response = document.getElementById('response');
      const button = document.querySelector('button');
      const flowerContainer = document.getElementById('flower-container');
      const music = document.getElementById('background-music');
      const image = document.getElementById('valentine-image');

      // Change the image to a GIF (use a direct GIF URL)
      image.src = "./good-morning.gif";

      // Show the response
      response.classList.remove('hidden');
      button.classList.add('hidden');
      // Create falling flower emojis
      for (let i = 0; i < 50; i++) {
        const flower = document.createElement('span');
        flower.classList.add('flower');
        flower.innerText = '🌸'; // Flower emoji
        flower.style.left = `${Math.random() * 100}%`;
        flower.style.animationDelay = `${Math.random() * 5}s`;
        flowerContainer.appendChild(flower);
      }

      // Show flower container
      flowerContainer.classList.remove('hidden');
      setTimeout(() => {
        music.currentTime = 20; // Start from 20s
        music.play();
      }, 500); // 0.5s delay to ensure it's ready
    }
  </script>
</body>
</html>
