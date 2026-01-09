<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Wedding Invitation</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Georgia', serif;
      background: linear-gradient(135deg, #f9f0e7, #f2d2bd);
      color: #333;
      line-height: 1.6;
    }

    .container {
      max-width: 900px;
      margin: 50px auto;
      padding: 20px;
      background: rgba(255, 255, 255, 0.9);
      border-radius: 15px;
      box-shadow: 0 8px 16px rgba(0,0,0,0.2);
      text-align: center;
      position: relative;
    }

    h1 {
      font-family: 'Cursive', sans-serif;
      font-size: 2.8em;
      margin-bottom: 10px;
      color: #b76e79;
      animation: pulse 2s infinite;
    }

    @keyframes pulse {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.05); }
    }

    .names {
      font-size: 2em;
      font-weight: bold;
      margin: 20px 0;
      color: #6b4f60;
      animation: slideIn 3s ease-out;
    }

    @keyframes slideIn {
      from { opacity: 0; transform: translateY(-20px); }
      to { opacity: 1; transform: translateY(0); }
    }

    p {
      font-size: 1.2em;
      margin: 10px 0;
    }

    .details {
      margin: 20px 0;
      font-size: 1.1em;
    }

    .countdown {
      font-size: 1.5em;
      margin: 15px 0;
      font-weight: bold;
      color: #d17f7f;
    }

    /* RSVP Form Styles */
    form {
      margin-top: 30px;
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    input[type="text"], input[type="email"] {
      padding: 10px;
      margin: 8px 0;
      border: 1px solid #ccc;
      border-radius: 8px;
      width: 250px;
      font-size: 1em;
    }

    button {
      padding: 10px 20px;
      margin-top: 12px;
      background-color: #b76e79;
      color: white;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      font-size: 1em;
      transition: background-color 0.3s;
    }

    button:hover {
      background-color: #a65d6a;
    }

    /* Optional: Add some decoration */
    .decor {
      width: 100px;
      margin: 20px auto;
    }

    .decor img {
      width: 100%;
    }

    @media(max-width: 600px){
      body {
        font-size: 16px;
      }
      h1 {
        font-size: 2em;
      }
    }
  </style>
</head>
<body>

  <div class="container">
    <div class="decor">
      <!-- Optional decorative image -->
      <!-- <img src="your-decorative-image.png" alt="Decor" /> -->
    </div>
    <h1>You're Invited</h1>
    <div class="names">
      Jonahjane & Edje
    </div>
    <p>To celebrate their wedding</p>
    <div class="details">
      <p>Date: <strong>June 20, 2026</strong></p>
      <p>Time: <strong>[Wedding Time]</strong></p>
      <p>Venue: <strong>Rica's Beach Resort, Anapog, San Remigio, Cebu</strong></p>
    </div>

    <!-- Countdown Timer -->
    <div class="countdown" id="countdown"></div>

    <!-- RSVP Form -->
    <h2>RSVP</h2>
    <form id="rsvpForm">
      <input type="text" id="name" placeholder="Your Name" required />
      <input type="email" id="email" placeholder="Your Email" required />
      <button type="submit">Send RSVP</button>
    </form>
    <div id="formMessage" style="margin-top:15px; color: green;"></div>
  </div>

  <script>
    // Set your wedding date here
    const weddingDate = new Date("2026-06-20T15:00:00"); // Adjust time as needed

    function updateCountdown() {
      const now = new Date();
      const diff = weddingDate - now;
      if (diff <= 0) {
        document.getElementById('countdown').innerHTML = "It's Wedding Day!";
        clearInterval(countdownInterval);
        return;
      }
      const days = Math.floor(diff / (1000 * 60 * 60 * 24));
      const hours = Math.floor((diff / (1000 * 60 * 60)) % 24);
      const minutes = Math.floor((diff / (1000 * 60)) % 60);
      const seconds = Math.floor((diff / 1000) % 60);

      document.getElementById('countdown').innerHTML = 
        `Wedding in ${days}d ${hours}h ${minutes}m ${seconds}s`;
    }

    const countdownInterval = setInterval(updateCountdown, 1000);
    updateCountdown();

    // Handle RSVP form submission
    document.getElementById('rsvpForm').addEventListener('submit', function(e) {
      e.preventDefault();
      const name = document.getElementById('name').value.trim();
      const email = document.getElementById('email').value.trim();

      // Here you could send data to your server or email service
      // For demo purposes, we'll just show a thank you message
      document.getElementById('formMessage').innerText = 
        `Thank you, ${name}! Your RSVP has been received.`;
      
      // Reset the form
      document.getElementById('rsvpForm').reset();
    });
  </script>

</body>
</html># Wedding-Invitation
