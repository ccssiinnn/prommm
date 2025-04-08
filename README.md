<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Prom Proposal Website</title>
  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;700&family=Sacramento&display=swap" rel="stylesheet">
  <style>
    /* Global Reset & Smooth Scrolling */
    * { margin: 0; padding: 0; box-sizing: border-box; }
    html { scroll-behavior: smooth; }
    body { font-family: 'Montserrat', sans-serif; line-height: 1.6; color: #fff; }
    
    /* Navigation Bar */
    nav {
      position: fixed;
      top: 0;
      width: 100%;
      background: rgba(0, 0, 0, 0.7);
      padding: 10px 20px;
      z-index: 100;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    nav .logo { font-family: 'Sacramento', cursive; font-size: 2rem; }
    nav ul { list-style: none; display: flex; gap: 20px; }
    nav ul li a { color: #fff; text-decoration: none; transition: color 0.3s; }
    nav ul li a:hover { color: #ff9a9e; }
    
    /* Section Styling */
    section { min-height: 100vh; padding: 80px 20px 40px; position: relative; }
    .section-content { max-width: 1200px; margin: auto; text-align: center; }
    
    /* Home Section */
    #home { background: #222; position: relative; overflow: hidden; }
    #particles-js { position: absolute; top: 0; left: 0; width: 100%; height: 100%; z-index: 1; }
    #hearts-container { position: absolute; top: 0; left: 0; width: 100%; height: 100%; pointer-events: none; z-index: 2; }
    #home .section-content { position: relative; z-index: 3; padding-top: 100px; }
    #home h1 {
      font-family: 'Sacramento', cursive;
      font-size: 4rem;
      margin-bottom: 20px;
      text-shadow: 2px 2px 5px #000;
      animation: popIn 1s ease-out forwards;
    }
    @keyframes popIn {
      from { transform: scale(0); opacity: 0; }
      to { transform: scale(1); opacity: 1; }
    }
    #home p { font-size: 1.5rem; margin-bottom: 40px; text-shadow: 1px 1px 3px #000; }
    
    /* Floating Hearts */
    .heart {
      position: absolute;
      width: 50px;
      height: 50px;
      background: red;
      transform: rotate(45deg);
      animation: float 8s linear infinite;
      opacity: 0.8;
    }
    .heart::before,
    .heart::after {
      content: "";
      position: absolute;
      width: 50px;
      height: 50px;
      background: red;
      border-radius: 50%;
    }
    .heart::before { top: -25px; left: 0; }
    .heart::after { left: 25px; top: 0; }
    @keyframes float {
      0% { transform: translateY(0) rotate(45deg); opacity: 0.8; }
      100% { transform: translateY(-120vh) rotate(45deg); opacity: 0; }
    }
    
    /* About Section */
    #about { background: #34495e; }
    #about h2 { font-size: 3rem; margin-bottom: 20px; }
    #about p { font-size: 1.2rem; max-width: 800px; margin: auto; }
    
    /* Proposal Section */
    #proposal { background: linear-gradient(135deg, #ff9a9e, #fad0c4); position: relative; overflow: hidden; }
    #proposal h2 {
      font-family: 'Sacramento', cursive;
      font-size: 3rem;
      margin-bottom: 10px;
      text-shadow: 2px 2px 5px #000;
      animation: fadeInDown 1.5s ease-out;
    }
    @keyframes fadeInDown {
      from { opacity: 0; transform: translateY(-20px); }
      to { opacity: 1; transform: translateY(0); }
    }
    #proposal p { font-size: 1.4rem; margin-bottom: 30px; }
    .button-container { display: flex; gap: 20px; justify-content: center; flex-wrap: wrap; }
    .btn {
      padding: 15px 30px;
      font-size: 1.1rem;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      transition: transform 0.2s, background-color 0.2s;
    }
    .btn:hover { transform: scale(1.05); }
    .yes { background-color: #27ae60; color: #fff; }
    .no { background-color: #e74c3c; color: #fff; }
    #proposal .message {
      margin-top: 30px;
      font-size: 1.8rem;
      opacity: 0;
      transition: opacity 0.5s;
      text-shadow: 1px 1px 3px #000;
    }
    #proposal .message.show { opacity: 1; }
    
    /* Gallery Section */
    #gallery { background: #2c3e50; }
    #gallery h2 { font-size: 3rem; margin-bottom: 20px; }
    .gallery-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 20px;
      max-width: 1200px;
      margin: auto;
    }
    .gallery-item {
      background: #fff;
      color: #333;
      border-radius: 8px;
      overflow: hidden;
      transition: transform 0.3s;
    }
    .gallery-item img {
      width: 100%;
      display: block;
    }
    .gallery-item:hover { transform: scale(1.05); }
    
    /* Footer */
    footer {
      background: #000;
      text-align: center;
      padding: 20px;
      font-size: 0.9rem;
      color: #aaa;
    }

    /* Confetti Canvas */
    #confetti-canvas {
      position: fixed;
      pointer-events: none;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: 999;
    }
  </style>
</head>
<body>
  <!-- Navigation -->
  <nav>
    <div class="logo">Prom Magic</div>
    <ul>
      <li><a href="#home">Home</a></li>
      <li><a href="#about">About</a></li>
      <li><a href="#proposal">Proposal</a></li>
      <li><a href="#gallery">Gallery</a></li>
    </ul>
  </nav>

  <!-- Home Section -->
  <section id="home">
    <div id="particles-js"></div>
    <div id="hearts-container"></div>
    <div class="section-content">
      <h1>Welcome to Our Story</h1>
      <p>Experience a magical journey leading to a special prom proposal.</p>
    </div>
  </section>

  <!-- About Section -->
  <section id="about">
    <div class="section-content">
      <h2>About Us</h2>
      <p>Every moment can be extraordinary. We celebrate love and unforgettable memories.
         Discover our journey and our passion for making life magical.</p>
    </div>
  </section>

  <!-- Proposal Section -->
  <section id="proposal">
    <div class="section-content">
      <h2>Will You Go to Prom With Me?</h2>
      <p>This isn’t just a question—it’s an invitation for an unforgettable night.
         I can’t wait to share this moment with you.</p>
      <div class="button-container">
        <button class="btn yes" id="yesBtn">Yes</button>
        <button class="btn no" id="noBtn">No</button>
      </div>
      <div class="message" id="proposal-message"></div>
    </div>
  </section>

  <!-- Gallery Section -->
  <section id="gallery">
    <div class="section-content">
      <h2>Our Gallery</h2>
      <div class="gallery-grid">
        <div class="gallery-item">
          <img src="https://via.placeholder.com/500x300?text=Memory+1" alt="Memory 1">
        </div>
        <div class="gallery-item">
          <img src="https://via.placeholder.com/500x300?text=Memory+2" alt="Memory 2">
        </div>
        <div class="gallery-item">
          <img src="https://via.placeholder.com/500x300?text=Memory+3" alt="Memory 3">
        </div>
        <div class="gallery-item">
          <img src="https://via.placeholder.com/500x300?text=Memory+4" alt="Memory 4">
        </div>
      </div>
    </div>
  </section>

  <!-- Footer -->
  <footer>
    &copy; 2025 Prom Magic. All rights reserved.
  </footer>

  <!-- Confetti Canvas -->
  <canvas id="confetti-canvas"></canvas>

  <!-- External Libraries -->
  <script src="https://cdn.jsdelivr.net/npm/particles.js@2.0.0/particles.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>

  <!-- Main JavaScript -->
  <script>
    document.addEventListener('DOMContentLoaded', function() {
      // Initialize particles background
      particlesJS("particles-js", {
        "particles": {
          "number": { "value": 80, "density": { "enable": true, "value_area": 800 } },
          "color": { "value": "#ffffff" },
          "shape": { "type": "circle" },
          "opacity": { "value": 0.5 },
          "size": { "value": 3, "random": true },
          "line_linked": {
            "enable": true,
            "distance": 150,
            "color": "#ffffff",
            "opacity": 0.4,
            "width": 1
          },
          "move": {
            "enable": true,
            "speed": 2,
            "direction": "none",
            "random": false,
            "straight": false,
            "out_mode": "out"
          }
        },
        "interactivity": {
          "detect_on": "canvas",
          "events": {
            "onhover": { "enable": true, "mode": "repulse" },
            "onclick": { "enable": true, "mode": "push" }
          },
          "modes": {
            "repulse": { "distance": 100 },
            "push": { "particles_nb": 4 }
          }
        },
        "retina_detect": true
      });

      // Create floating hearts
      const heartsContainer = document.getElementById('hearts-container');
      for (let i = 0; i < 20; i++) {
        const heart = document.createElement('div');
        heart.classList.add('heart');
        heart.style.left = Math.random() * 100 + '%';
        heart.style.animationDelay = Math.random() * 8 + 's';
        heart.style.width = heart.style.height = (Math.random() * 20 + 30) + 'px';
        heartsContainer.appendChild(heart);
      }

      // Bind confetti to the canvas
      const confettiCanvas = document.getElementById('confetti-canvas');
      const myConfetti = confetti.create(confettiCanvas, { resize: true, useWorker: true });

      // Proposal Section: Button interactions
      const yesBtn = document.getElementById('yesBtn');
      const noBtn = document.getElementById('noBtn');
      const proposalMessage = document.getElementById('proposal-message');

      yesBtn.addEventListener('click', function() {
        proposalMessage.textContent = 'Yay! I knew you would say yes! Prepare for an unforgettable night!';
        proposalMessage.classList.add('show');
        myConfetti({ particleCount: 200, spread: 70, origin: { y: 0.6 } });
      });

      noBtn.addEventListener('mouseover', function() {
        const randomX = Math.random() * 300 - 150;
        const randomY = Math.random() * 300 - 150;
        noBtn.style.transform = `translate(${randomX}px, ${randomY}px)`;
      });

      noBtn.addEventListener('click', function() {
        const randomX = Math.random() * 300 - 150;
        const randomY = Math.random() * 300 - 150;
        noBtn.style.transform = `translate(${randomX}px, ${randomY}px)`;
      });
    });
  </script>
</body>
</html>
