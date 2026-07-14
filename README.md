<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>stress relief · main menu</title>
  <!-- Apple Font (SF Pro) via system font stack -->
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      background: #0b0b0b;
      font-family: -apple-system, BlinkMacSystemFont, "SF Pro Display", "SF Pro Text", "Helvetica Neue", system-ui, sans-serif;
      padding: 1rem;
    }

    /* main card – black background with subtle moving effect */
    .menu-card {
      position: relative;
      background: #0a0a0a;
      max-width: 780px;
      width: 100%;
      padding: 3rem 2.5rem;
      border-radius: 48px;
      box-shadow: 0 25px 40px -12px rgba(0, 0, 0, 0.9), 0 0 0 1px rgba(255, 255, 255, 0.02);
      overflow: hidden;
      transition: box-shadow 0.2s;
      text-align: center;
      backdrop-filter: blur(1px);
    }

    /* moving background effect – minimal, smooth drift */
    .menu-card::before {
      content: '';
      position: absolute;
      inset: -20px;
      z-index: 0;
      background: 
        radial-gradient(circle at 20% 30%, rgba(110, 130, 255, 0.06) 0%, transparent 40%),
        radial-gradient(circle at 80% 70%, rgba(255, 180, 220, 0.05) 0%, transparent 45%),
        radial-gradient(circle at 40% 80%, rgba(180, 220, 255, 0.04) 0%, transparent 50%);
      background-blend-mode: overlay;
      animation: slowDrift 16s infinite alternate ease-in-out;
      pointer-events: none;
    }

    /* second subtle layer – extra moving grain */
    .menu-card::after {
      content: '';
      position: absolute;
      inset: -10px;
      z-index: 0;
      background: 
        repeating-linear-gradient(45deg, rgba(255, 255, 255, 0.008) 0px, rgba(255, 255, 255, 0.008) 2px, transparent 2px, transparent 8px);
      opacity: 0.2;
      animation: subtleSlide 22s infinite alternate ease-in-out;
      pointer-events: none;
    }

    /* keyframes – minimal movement */
    @keyframes slowDrift {
      0% { transform: scale(1) translate(0px, 0px); opacity: 0.7; }
      100% { transform: scale(1.02) translate(12px, -8px); opacity: 1; }
    }

    @keyframes subtleSlide {
      0% { transform: translateX(-6px) translateY(4px) scale(1); }
      100% { transform: translateX(12px) translateY(-6px) scale(1.02); }
    }

    /* all content sits above the moving layers */
    .menu-content {
      position: relative;
      z-index: 2;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 1.2rem;
    }

    /* medium size text */
    .headline {
      font-size: 2.1rem;
      font-weight: 600;
      letter-spacing: -0.02em;
      color: #f5f5f7;
      text-shadow: 0 2px 12px rgba(0, 0, 0, 0.8);
      line-height: 1.2;
      max-width: 700px;
      margin-bottom: 0.2rem;
    }

    /* description – apple style, lighter weight */
    .description {
      font-size: 1.2rem;
      font-weight: 400;
      color: #b0b0b8;
      max-width: 560px;
      line-height: 1.5;
      letter-spacing: -0.01em;
      text-shadow: 0 1px 6px rgba(0, 0, 0, 0.7);
      margin-bottom: 0.6rem;
    }

    /* button group */
    .button-group {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      justify-content: center;
      gap: 1.2rem;
      margin-top: 1.2rem;
      width: 100%;
    }

    /* button base – apple style */
    .btn {
      font-family: inherit;
      font-size: 1.1rem;
      font-weight: 500;
      padding: 0.8rem 2.5rem;
      border-radius: 60px;
      border: none;
      cursor: pointer;
      background: #ffffff;
      color: #0a0a0a;
      transition: all 0.2s ease;
      box-shadow: 0 6px 16px rgba(0, 0, 0, 0.5), 0 0 0 1px rgba(255, 255, 255, 0.03);
      letter-spacing: -0.01em;
      min-width: 140px;
      backdrop-filter: blur(4px);
      background: rgba(255, 255, 255, 0.96);
    }

    .btn-login {
      background: #ffffff;
      color: #0a0a0a;
    }

    .btn-login:hover {
      background: #f0f0f2;
      transform: scale(1.02);
      box-shadow: 0 10px 24px rgba(0, 0, 0, 0.6);
    }

    .btn-signup {
      background: #e8e8ed;
      color: #0a0a0a;
      box-shadow: 0 6px 16px rgba(0, 0, 0, 0.4), 0 0 0 1px rgba(255, 255, 255, 0.05);
    }

    .btn-signup:hover {
      background: #dcdce2;
      transform: scale(1.02);
      box-shadow: 0 10px 24px rgba(0, 0, 0, 0.6);
    }

    .btn:active {
      transform: scale(0.97);
    }

    /* tiny extra polish */
    .fine-print {
      margin-top: 1rem;
      font-size: 0.8rem;
      color: #55555e;
      letter-spacing: 0.2px;
      opacity: 0.5;
      z-index: 2;
      position: relative;
    }

    /* responsive */
    @media (max-width: 480px) {
      .menu-card {
        padding: 2rem 1.5rem;
        border-radius: 32px;
      }
      .headline {
        font-size: 1.7rem;
      }
      .description {
        font-size: 1rem;
      }
      .btn {
        padding: 0.7rem 1.8rem;
        min-width: 120px;
        font-size: 1rem;
      }
      .button-group {
        gap: 0.9rem;
      }
    }

    /* interactive buttons – they work! (demo actions) */
    .btn-login:active, .btn-signup:active {
      background: #c0c0c8;
      transition: 0.05s;
    }
  </style>
</head>
<body>
  <div class="menu-card">
    <div class="menu-content">
      <!-- medium size headline -->
      <h1 class="headline">Are You Stressed?<br>You Clicked On The Right Website!</h1>
      
      <!-- description -->
      <p class="description">
        This website was made to help you with relieving stress and making you feel better again.
      </p>

      <!-- login + signup buttons (functional) -->
      <div class="button-group">
        <button class="btn btn-login" id="loginBtn">Log In</button>
        <button class="btn btn-signup" id="signupBtn">Sign Up</button>
      </div>

      <!-- subtle extra text (just for design) -->
      <div class="fine-print">⏤  find your calm  ⏤</div>
    </div>
  </div>

  <script>
    (function() {
      // --- make buttons truly interactive ---

      const loginBtn = document.getElementById('loginBtn');
      const signupBtn = document.getElementById('signupBtn');

      // login handler
      loginBtn.addEventListener('click', function(e) {
        e.preventDefault();
        // simple demo: show an alert (simulates login flow)
        alert('🔓 Log in clicked.\n(You would be redirected to your account.)');
        // you could replace with: window.location.href = '/login';
      });

      // signup handler
      signupBtn.addEventListener('click', function(e) {
        e.preventDefault();
        alert('✨ Sign up clicked.\n(Redirect to registration page.)');
        // you could replace with: window.location.href = '/signup';
      });

      // extra: keyboard support & ARIA (already interactive)
      console.log('✅ menu ready – buttons work.');
    })();
  </script>

  <!-- ensure apple font is applied via system stack (already set in body) -->
</body>
</html>
