<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Peeep</title>
  <!-- <link href="https://fonts.googleapis.com/css2?family=Press+Start+2P&family=Space+Mono:ital,wght@0,400;0,700;1,400&display=swap" rel="stylesheet" /> -->
  <style>
    *, *::before, *::after {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    :root {
      --pink-bg: #f5e0e8;
      --pink-light: #fdf0f5;
      --text-dark: #111111;
      --text-muted: #8a9cc2;
      --text-body: #da0e8f;
      --border: #111111;
      --btn-bg: #ffffff;
      --btn-shadow: #c8a8b8;
    }

    html, body {
      height: 100%;
    }

    body {
      background-color: var(--pink-bg);
      font-family: 'Space Mono', monospace;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      min-height: 100vh;
      padding: 2rem 1.5rem;
      position: relative;
      overflow-x: hidden;
    }

    /* Subtle noise texture overlay */
    body::before {
      content: '';
      position: fixed;
      inset: 0;
      background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.03'/%3E%3C/svg%3E");
      background-size: 200px 200px;
      pointer-events: none;
      z-index: 0;
    }

    .container {
      position: relative;
      z-index: 1;
      display: flex;
      flex-direction: column;
      align-items: center;
      text-align: center;
      max-width: 600px;
      width: 100%;
      animation: fadeUp 0.8s ease both;
    }

    .logo-img {
      display: block;
      max-width: 200px !important;
      height: auto;
      background: transparent !important;
      padding-bottom: 4rem;
    }

    /* Star */
    .star-wrapper {
      animation: floatStar 4s ease-in-out infinite;
    }

    .star-wrapper img,
    .star-wrapper .star-png {
      width: 200px;
      height: 200px;
      display: block;
      background: transparent;
    }

    /* CSS 3D metallic star fallback */
    .star-png {
      mix-blend-mode: multiply;
      filter: drop-shadow(0 8px 24px rgba(30, 26, 26, 0.4)) drop-shadow(0 2px 4px rgba(0,0,0,0.4));
    }

    /* Title */
    .title {
      font-family: 'Press Start 2P', monospace;
      font-size: clamp(2.4rem, 8vw, 3.8rem);
      color: var(--text-dark);
      letter-spacing: -0.01em;
      margin-bottom: 3rem;
      line-height: 1.15;
      animation: fadeUp 0.8s 0.15s ease both;
    }

    /* Copy */
    .headline {
      font-family: 'Space Mono', monospace;
      font-size: clamp(0.85rem, 2.5vw, 1rem);
      color: var(--text-muted);
      letter-spacing: 0.04em;
      margin-bottom: 2rem;
      animation: fadeUp 0.8s 0.25s ease both;
    }

    .body-copy {
      font-family: 'Space Mono', monospace;
      font-size: clamp(0.78rem, 2.2vw, 0.9rem);
      color: var(--text-body);
      line-height: 1.75;
      letter-spacing: 0.02em;
      margin-bottom: 2.2rem;
      animation: fadeUp 0.8s 0.35s ease both;
    }

    /* Form */
    .form-group {
      width: 100%;
      max-width: 420px;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 0.85rem;
      animation: fadeUp 0.8s 0.45s ease both;
    }

    .email-input {
      width: 100%;
      font-family: 'Space Mono', monospace;
      font-size: 0.8rem;
      letter-spacing: 0.04em;
      color: var(--text-dark);
      background: rgba(255,255,255,0.7);
      border: 1.5px solid var(--border);
      border-radius: 8px;
      padding: 0.85rem 1.2rem;
      outline: none;
      transition: background 0.2s, box-shadow 0.2s;
    }

    .email-input::placeholder {
      color: #bbb;
    }

    .email-input:focus {
      background: rgba(255,255,255,0.95);
      box-shadow: 0 0 0 5px rgba(245, 95, 190, 0.38);
    }

    .btn {
      font-family: 'Space Mono', monospace;
      font-size: 0.78rem;
      letter-spacing: 0.06em;
      color: var(--text-dark);
      background: var(--btn-bg);
      border: 1.5px solid var(--border);
      border-radius: 30px;
      padding: 0.75rem 2.4rem;
      cursor: pointer;
      transition: transform 0.15s, box-shadow 0.15s, background 0.15s;
      box-shadow: 2px 3px 0 var(--btn-shadow);
      margin-bottom: 2rem;
    }

    .btn:hover {
      transform: translate(-1px, -1px);
      box-shadow: 4px 5px 0 var(--btn-shadow);
    }

    .btn:active {
      transform: translate(1px, 1px);
      box-shadow: 1px 1px 0 var(--btn-shadow);
    }

    /* Success state */
    .success-msg {
      display: none;
      font-family: 'Space Mono', monospace;
      font-size: 0.8rem;
      color: var(--text-body);
      letter-spacing: 0.04em;
      animation: fadeUp 0.4s ease both;
    }

    .success-msg.visible {
      display: block;
    }

    /* Disclaimer */
    .disclaimer {
      margin-top: 2rem;
      font-family: 'Space Mono', monospace;
      font-size: 0.65rem;
      color: var(--text-muted);
      letter-spacing: 0.04em;
      animation: fadeUp 0.8s 0.55s ease both;
    }

    /* Animations */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(18px); }
      to   { opacity: 1; transform: translateY(0); }
    }

    @keyframes floatStar {
      0%, 100% { transform: translateY(0) rotate(-2deg); }
      50%       { transform: translateY(-10px) rotate(2deg); }
    }

    /* Responsive tweaks */
    @media (max-width: 480px) {
      .star-wrapper .star-png {
        width: 100px;
        height: 100px;
      }
      .title {
        font-size: 2rem;
      }
      .form-group {
        max-width: 100%;
      }
    }
  </style>
</head>
<body>

  <div class="container">

    <!-- 3D-style metallic star PNG -->
    <div class="star-wrapper">
    <img class="star-png" src="/images_icons/shiny-star.png?v=20260327b">
    </div>

    <img class="logo-img" src="/images_icons/peeep-logo.png?v=20260327b">

    <p class="headline">Something exciting is coming!</p>
    <p class="body-copy">
      Be the first to know when we launch.<br/>
      Sign up for our newsletter and we'll keep<br/>
      you in the loop.
    </p>

    <div class="form-group" id="formGroup">
      <input
        class="email-input"
        type="email"
        id="emailInput"
        placeholder="enter your email address"
        autocomplete="email"
      />
      <button class="btn" onclick="handleSubmit()">notify me</button>
    </div>

    <p class="success-msg" id="successMsg">✦ you're on the list — we'll be in touch! ✦</p>

    <p class="disclaimer">No spam ever, unsubscribe at any time</p>
  </div>

  <script>
    function handleSubmit() {
      const input = document.getElementById('emailInput');
      const formGroup = document.getElementById('formGroup');
      const successMsg = document.getElementById('successMsg');

      const email = input.value.trim();
      const valid = /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email);

      if (!valid) {
        input.style.borderColor = '#e08080';
        input.style.boxShadow = '0 0 0 3px rgba(220,100,100,0.15)';
        input.focus();
        setTimeout(() => {
          input.style.borderColor = '';
          input.style.boxShadow = '';
        }, 1800);
        return;
      }

      formGroup.style.opacity = '0';
      formGroup.style.transform = 'translateY(6px)';
      formGroup.style.transition = 'opacity 0.3s, transform 0.3s';

      setTimeout(() => {
        formGroup.style.display = 'none';
        successMsg.classList.add('visible');
      }, 300);
    }

    document.getElementById('emailInput').addEventListener('keydown', function(e) {
      if (e.key === 'Enter') handleSubmit();
    });
  </script>
</body>
</html>