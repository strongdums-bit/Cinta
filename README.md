<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Our Special Day</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Poppins', sans-serif;
    }

    body {
      background: #090714;
      color: #ffffff;
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      overflow-x: hidden;
      position: relative;
    }

    /* Efek Background Latar Bintang / Partikel */
    .stars-bg {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: radial-gradient(ellipse at bottom, #1b1335 0%, #090714 100%);
      z-index: -1;
    }

    .container {
      width: 100%;
      max-width: 450px;
      padding: 20px;
      text-align: center;
      position: relative;
      z-index: 2;
    }

    .step {
      display: none;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      animation: fadeIn 0.6s ease-in-out forwards;
    }

    .step.active {
      display: flex;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: scale(0.95); }
      to { opacity: 1; transform: scale(1); }
    }

    /* Judul & Teks */
    h1.main-title {
      font-size: 1.8rem;
      font-weight: 700;
      color: #ffffff;
      margin-bottom: 8px;
      text-shadow: 0 0 10px rgba(255, 255, 255, 0.3);
    }

    p.sub-title {
      font-size: 0.85rem;
      color: #a0a0c0;
      margin-bottom: 20px;
    }

    /* Tombol Interaktif Presisi Video */
    .btn-action {
      margin-top: 25px;
      padding: 12px 30px;
      font-size: 0.9rem;
      font-weight: 600;
      color: #ffffff;
      background: linear-gradient(135deg, #e91e63, #9c27b0);
      border: none;
      border-radius: 25px;
      cursor: pointer;
      box-shadow: 0 4px 15px rgba(233, 30, 99, 0.4);
      display: inline-flex;
      align-items: center;
      gap: 8px;
      transition: all 0.3s ease;
    }

    .btn-action:hover {
      transform: translateY(-2deg);
      box-shadow: 0 6px 20px rgba(233, 30, 99, 0.6);
    }

    /* STEP 1: COUNTDOWN TIMER */
    .timer-container {
      display: flex;
      gap: 12px;
      margin: 20px 0;
    }

    .timer-card {
      background: rgba(255, 255, 255, 0.05);
      border: 1px solid rgba(255, 255, 255, 0.1);
      padding: 10px 14px;
      border-radius: 10px;
      min-width: 65px;
    }

    .timer-card .num {
      font-size: 1.6rem;
      font-weight: 700;
      color: #ff4081;
    }

    .timer-card .label {
      font-size: 0.65rem;
      color: #888;
      text-transform: uppercase;
    }

    /* STEP 2: GIFT BOX */
    .gift-container {
      margin: 30px 0;
      cursor: pointer;
    }

    .gift-icon {
      font-size: 4.5rem;
      color: #ff4081;
      animation: pulse 1.5s infinite;
    }

    @keyframes pulse {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.1); }
    }

    /* STEP 3: FLOATING POLAROID SIDE FRAMES */
    .floating-polaroids {
      position: absolute;
      width: 100%;
      height: 100%;
      top: 0;
      left: 0;
      pointer-events: none;
    }

    .pol-side {
      position: absolute;
      width: 60px;
      height: 75px;
      background: #fff;
      padding: 4px 4px 12px 4px;
      border-radius: 3px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.5);
    }

    .pol-side img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    .p-left-1 { top: 10%; left: -10px; transform: rotate(-15deg); }
    .p-left-2 { top: 40%; left: -15px; transform: rotate(10deg); }
    .p-left-3 { top: 70%; left: -10px; transform: rotate(-8deg); }
    .p-right-1 { top: 12%; right: -10px; transform: rotate(12deg); }
    .p-right-2 { top: 42%; right: -15px; transform: rotate(-10deg); }
    .p-right-3 { top: 72%; right: -10px; transform: rotate(15deg); }

    /* STEP 4: SURAT UCAPAN (LETTER) */
    .letter-card {
      background: rgba(255, 255, 255, 0.04);
      border: 1px solid rgba(255, 255, 255, 0.1);
      backdrop-filter: blur(12px);
      border-radius: 16px;
      padding: 20px;
      text-align: left;
      max-height: 380px;
      overflow-y: auto;
      box-shadow: 0 10px 30px rgba(0,0,0,0.5);
    }

    .letter-card p {
      font-size: 0.85rem;
      line-height: 1.7;
      color: #d1d1e0;
      margin-bottom: 12px;
    }

    /* STEP 5: GALERI 8 FOTO POLAROID */
    .gallery-grid {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 12px;
      max-height: 380px;
      overflow-y: auto;
      padding: 8px;
      width: 100%;
    }

    .polaroid-item {
      background: #ffffff;
      padding: 6px 6px 18px 6px;
      border-radius: 4px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.4);
    }

    .polaroid-item img {
      width: 100%;
      height: 110px;
      object-fit: cover;
      border-radius: 2px;
    }

    /* STEP 6: PEMUTAR VIDEO */
    .video-box {
      width: 100%;
      border-radius: 12px;
      overflow: hidden;
      box-shadow: 0 8px 20px rgba(0,0,0,0.6);
      margin-top: 15px;
    }

    .video-box video {
      width: 100%;
      display: block;
    }
  </style>
</head>
<body>

  <div class="stars-bg"></div>

  <div class="container">

    <div class="step active" id="step-1">
      <h1 class="main-title">Our Most Beautiful Story</h1>
      <p class="sub-title">Her Special Day is Coming</p>
      
      <div class="timer-container">
        <div class="timer-card"><div class="num">00</div><div class="label">Days</div></div>
        <div class="timer-card"><div class="num">00</div><div class="label">Hours</div></div>
        <div class="timer-card"><div class="num">00</div><div class="label">Mins</div></div>
        <div class="timer-card"><div class="num" id="sec-num">05</div><div class="label">Secs</div></div>
      </div>

      <button class="btn-action" id="btn-step-1" style="display: none;" onclick="goToStep(2)">
        OPEN HER GIFT <i class="fa-solid fa-gift"></i>
      </button>
    </div>

    <div class="step" id="step-2">
      <h1 class="main-title">ADA SESUATU UNTUKMU</h1>
      <p class="sub-title">klik untuk membuka konfeti</p>
      
      <div class="gift-container" onclick="goToStep(3)">
        <i class="fa-solid fa-box-open gift-icon"></i>
      </div>
    </div>

    <div class="step" id="step-3">
      <div class="floating-polaroids">
        <div class="pol-side p-left-1"><img src="https://drive.google.com/thumbnail?id=1M0tfGeWhqaExHNJt8XbCIRB7xaX4OLxl&sz=w800"></div>
        <div class="pol-side p-left-2"><img src="https://drive.google.com/thumbnail?id=1FxRH9WOmlZP3t7T8REgmtIs9qBZm4eK3&sz=w800"></div>
        <div class="pol-side p-left-3"><img src="https://drive.google.com/thumbnail?id=1KmtIFNe5dYrdrP7GBowK8yvRC_jIZEeb&sz=w800"></div>
        <div class="pol-side p-right-1"><img src="https://drive.google.com/thumbnail?id=1SLnDacS3fqC6tQ_zGWFtHKi7LdxU4MUN&sz=w800"></div>
        <div class="pol-side p-right-2"><img src="https://drive.google.com/thumbnail?id=1Wg2lKpoiAa_L1KnirliJisAA7eTFt_Q4&sz=w800"></div>
        <div class="pol-side p-right-3"><img src="https://drive.google.com/thumbnail?id=11Sk1EDqHjtKnVaR2qw2FPcFpkhYm022W&sz=w800"></div>
      </div>

      <h1 class="main-title">Our Special Day</h1>
      <p class="sub-title">Created with love, just for you</p>
      
      <button class="btn-action" onclick="goToStep(4)">
        READ MY LETTER <i class="fa-solid fa-envelope"></i>
      </button>
    </div>

    <div class="step" id="step-4">
      <h1 class="main-title" style="font-size: 1.4rem;">Happy Birthday Sayangkuuu ❤️</h1>
      
      <div class="letter-card">
        <p>Haii... sayangku, hari dimana ternyata kita bersatu dan waktu dimana kita selalu menikmati momen kebersamaan, semoga semua harapan, keinginan, tujuan, doa kita terkabulkan semua nya dan semoga kita selalu sukses dalam hal yang kita inginkan.</p>
        <p>Hidup kita itu seperti makhluk hidup di bumi dan bumi karena mereka saling membutuhkan untuk selalu melengkapi.</p>
        <p>Sayang.... Thank you banget selalu mewarnai hari-hariku ❤️</p>
        <p>Apapun badai nanti kita harus hadapi dan semoga Allah kasih kita kemudahan dan kesuksesan yang besar dan semoga kalau bisa ngak ada badai 😆 dan semoga nantinya bersatu nya kita membawa kebaikan kepada keluarga kita nanti dan kepada kedua orang tua kita.</p>
        <p style="font-weight: 700; color: #ff4081;">I LOVE U SAYANG.....</p>
      </div>

      <button class="btn-action" onclick="goToStep(5)">
        OUR MEMORIES <i class="fa-solid fa-camera"></i>
      </button>
    </div>

    <div class="step" id="step-5">
      <h1 class="main-title">Our Memories</h1>
      <p class="sub-title">every moment captured in love</p>

      <div class="gallery-grid">
        <div class="polaroid-item"><img src="https://drive.google.com/thumbnail?id=1FgzyessLSMn2sRQEu3hBItQoOs4GTxMq&sz=w800"></div>
        <div class="polaroid-item"><img src="https://drive.google.com/thumbnail?id=1JW4ijGOvY99Gp9v6KEL444L99jThWpN2&sz=w800"></div>
        <div class="polaroid-item"><img src="https://drive.google.com/thumbnail?id=1fOBPJPn692ShXacsTROeq0gw3vvdw-da&sz=w800"></div>
        <div class="polaroid-item"><img src="https://drive.google.com/thumbnail?id=1TsAW7-HjEZJtmLxQ9qMDhWOtCFXD-Urn&sz=w800"></div>
        <div class="polaroid-item"><img src="https://drive.google.com/thumbnail?id=1Pusu9btwRZz1STpi7w198Ls5kZUThDJt&sz=w800"></div>
        <div class="polaroid-item"><img src="https://drive.google.com/thumbnail?id=1O9E_lgev0KhgORvf9YHTs_-KmoH1EzS1&sz=w800"></div>
        <div class="polaroid-item"><img src="https://drive.google.com/thumbnail?id=1XXxEOmkyDgfh_cEbqCKuojb5avJ_fj10&sz=w800"></div>
        <div class="polaroid-item"><img src="https://drive.google.com/thumbnail?id=1gF8_N6-w0Ia0_0Z9Vwc80C48dDaHbWBo&sz=w800"></div>
      </div>

      <button class="btn-action" onclick="goToStep(6)">
        WATCH VIDEO <i class="fa-solid fa-video"></i>
      </button>
    </div>

    <div class="step" id="step-6">
      <h1 class="main-title">A Moment For You</h1>
      <p class="sub-title">a special video message</p>

      <div class="video-box">
        <video id="main-video" controls poster="https://drive.google.com/thumbnail?id=1FgzyessLSMn2sRQEu3hBItQoOs4GTxMq&sz=w800">
          <source src="https://collection.cloudinary.com/djir8qxd/eb6462693183713bfc68d86afbc7c0b1" type="video/mp4">
        </video>
      </div>

      <button class="btn-action" onclick="goToStep(7)">
        LOVE <i class="fa-solid fa-heart"></i>
      </button>
    </div>

    <div class="step" id="step-7">
      <h1 class="main-title" style="font-size: 1.3rem;">Our Best Day & Our Beloved Moments</h1>
      
      <p style="margin: 30px 0; font-size: 0.95rem; color: #ffb7c5; line-height: 1.6;">
        "May we be united, succeed together, and always be under Allah's blessings and grace."
      </p>

      <button class="btn-action" onclick="restart()">
        REPLAY FROM START <i class="fa-solid fa-rotate-right"></i>
      </button>
    </div>

  </div>

  <script>
    // Timer Hitung Mundur dari 5 Detik
    let count = 5;
    const secNum = document.getElementById('sec-num');
    const btnStep1 = document.getElementById('btn-step-1');

    const timer = setInterval(() => {
      count--;
      secNum.innerText = count < 10 ? `0${count}` : count;
      
      if (count <= 0) {
        clearInterval(timer);
        btnStep1.style.display = 'inline-flex';
      }
    }, 1000);

    // Fungsi Alur Pindah Step
    function goToStep(stepNumber) {
      document.querySelectorAll('.step').forEach(el => el.classList.remove('active'));
      document.getElementById(`step-${stepNumber}`).classList.add('active');

      if (stepNumber !== 6) {
        const vid = document.getElementById('main-video');
        if (vid) vid.pause();
      }
    }

    // Reset Ke Awal
    function restart() {
      goToStep(1);
      count = 5;
      secNum.innerText = "05";
      btnStep1.style.display = 'none';
      
      const timerRestart = setInterval(() => {
        count--;
        secNum.innerText = count < 10 ? `0${count}` : count;
        if (count <= 0) {
          clearInterval(timerRestart);
          btnStep1.style.display = 'inline-flex';
        }
      }, 1000);
    }
  </script>
</body>
</html>
