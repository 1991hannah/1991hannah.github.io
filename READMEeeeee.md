<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Peeep — Coming Soon</title>
  <style>
    *, *::before, *::after {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      background: #fae6f0 100%;
      font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
      color: #ffffff;
    }

    .container {
      text-align: center;
      padding: 2rem;
      max-width: 560px;
      width: 100%;
    }

    .logo-img {
      display: block;
      margin: 0 auto 0.5rem;
      max-width: 180px;
      width: 100%;
      height: auto;
      background: transparent !important;
    }

    .logo {
      font-size: 3rem;
      font-weight: 800;
      letter-spacing: -1px;
      margin-bottom: 1rem;
      background: linear-gradient(90deg, #e94560, #f5a623);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }

    .tagline {
      font-size: 1.25rem;
      color: #a8b2d8;
      margin-bottom: 0.5rem;
    }

    .description {
      font-size: 0.95rem;
      color: #6b7db3;
      margin-bottom: 2.5rem;
      line-height: 1.6;
    }

    .signup-form {
      display: flex;
      flex-direction: column;
      gap: 0.75rem;
    }

    .input-row {
      display: flex;
      gap: 0.5rem;
    }

    .email-input {
      flex: 1;
      padding: 0.85rem 1.25rem;
      border: 2px solid rgba(255, 255, 255, 0.1);
      border-radius: 8px;
      background: rgba(255, 255, 255, 0.07);
      color: #ffffff;
      font-size: 1rem;
      outline: none;
      transition: border-color 0.2s;
    }

    .email-input::placeholder {
      color: #6b7db3;
    }

    .email-input:focus {
      border-color: #e94560;
    }

    .submit-btn {
      padding: 0.85rem 1.75rem;
      background: linear-gradient(90deg, #e94560, #f5a623);
      border: none;
      border-radius: 8px;
      color: #ffffff;
      font-size: 1rem;
      font-weight: 600;
      cursor: pointer;
      transition: opacity 0.2s, transform 0.1s;
      white-space: nowrap;
    }

    .submit-btn:hover {
      opacity: 0.9;
      transform: translateY(-1px);
    }

    .submit-btn:active {
      transform: translateY(0);
    }

    .message {
      font-size: 0.9rem;
      min-height: 1.4em;
      transition: color 0.2s;
    }

    .message.success {
      color: #64d9a0;
    }

    .message.error {
      color: #e94560;
    }

    .privacy-note {
      margin-top: 1.25rem;
      font-size: 0.8rem;
      color: #4a5578;
    }

    .sr-only {
      position: absolute;
      width: 1px;
      height: 1px;
      padding: 0;
      margin: -1px;
      overflow: hidden;
      clip: rect(0, 0, 0, 0);
      white-space: nowrap;
      border: 0;
    }

    @media (max-width: 480px) {
      .input-row {
        flex-direction: column;
      }

      .logo {
        font-size: 2.25rem;
      }
    }
  </style>
</head>
<body>
  <main class="container">
  <img class="logo-img" src="/images_icons/peeep-logo.png?v=20260327b">
  <img src="/images_icons/shiny-star-pink.png">
    <h1 class="logo">Peeep</h1>
    <p class="tagline">Something exciting is coming.</p>
    <p class="description">
      Be the first to know when we launch.<br />
      Sign up for our newsletter and we'll keep you in the loop.
    </p>

    <form class="signup-form" id="signup-form" novalidate>
      <div class="input-row">
        <label for="email" class="sr-only">Email address</label>
        <input
          type="email"
          id="email"
          name="email"
          class="email-input"
          placeholder="Enter your email address"
          autocomplete="email"
          required
        />
        <button type="submit" class="submit-btn">Notify Me</button>
      </div>
    </form>
    <img src="/images_icons/icons/instagram.svg>
  </main>

  <script>
    (function () {
      var form = document.getElementById('signup-form');
      var emailInput = document.getElementById('email');
      var message = document.getElementById('form-message');
      var emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;

      form.addEventListener('submit', function (event) {
        event.preventDefault();
        message.className = 'message';
        message.textContent = '';

        var email = emailInput.value.trim();

        if (!email || !emailPattern.test(email)) {
          message.className = 'message error';
          message.textContent = 'Please enter a valid email address.';
          emailInput.focus();
          return;
        }

        // Simulate a successful signup (replace with real backend/service call)
        message.className = 'message success';
        message.textContent = 'You\u2019re on the list! We\u2019ll be in touch soon.';
        emailInput.value = '';
      });
    })();
  </script>
</body>
</html>
