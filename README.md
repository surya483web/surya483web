<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GV SAFE SITE CONSTRUCTION CAMERAS</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700&display=swap');
        body {
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 0;
            background: linear-gradient(135deg, #001f3f, #007bff, #00c3ff);
            color: white;
            text-align: center;
        }
        header {
            padding: 20px;
            background: rgba(0, 0, 0, 0.7);
            font-family: 'Orbitron', sans-serif;
            font-size: 28px;
            letter-spacing: 3px;
        }
        .top-right-menu {
            position: absolute;
            top: 10px;
            right: 20px;
            cursor: pointer;
            font-size: 24px;
            background: #ffcc00;
            padding: 5px 10px;
            border-radius: 5px;
            color: black;
        }
        .menu-content {
            display: none;
            position: absolute;
            right: 20px;
            top: 50px;
            background: rgba(0, 0, 0, 0.8);
            padding: 10px;
            border-radius: 5px;
        }
        .menu-content a {
            display: block;
            color: white;
            text-decoration: none;
            padding: 5px;
        }
        .container {
            padding: 50px;
            background: url('https://source.unsplash.com/1600x900/?cctv,security') no-repeat center center/cover;
            min-height: 60vh;
        }
        .features {
            padding: 20px;
            background: rgba(0, 0, 0, 0.5);
        }
        .dashboard {
            padding: 20px;
            background: #222;
            display: flex;
            justify-content: space-around;
            flex-wrap: wrap;
        }
        .dashboard div {
            background: #444;
            padding: 20px;
            width: 30%;
            margin: 10px;
            border-radius: 10px;
            cursor: pointer;
            transition: 0.3s;
            box-shadow: 0 0 10px rgba(255, 255, 255, 0.3);
        }
        .dashboard div:hover {
            box-shadow: 0 0 20px rgba(255, 255, 255, 0.6);
        }
        .review-section {
            display: none;
            padding: 20px;
            background: #333;
            border-radius: 10px;
        }
    </style>
</head>
<body>
    <header>
        <h1>📷 GV SAFE SITE CONSTRUCTION CAMERAS 📷</h1>
        <div class="top-right-menu" onclick="toggleMenu()">☰</div>
        <div class="menu-content" id="menuContent">
            <a href="#" onclick="showAbout()">About Us</a>
            <a href="#contact">Contact Us</a>
            <a href="mailto:surya.murali109@gmail.com">Email</a>
            <a href="https://wa.me/9342792571">WhatsApp</a>
        </div>
    </header>
    <div class="container">
        <h2>24/7 Surveillance | AI-powered Monitoring | High-Resolution CCTV</h2>
        <p>Secure your site with the best-in-class CCTV solutions, ensuring safety and real-time monitoring.</p>
        <div class="features">
            <p>✔ Live HD Streaming | ✔ Motion Detection | ✔ Cloud Storage</p>
        </div>
        <div class="contact">Call Us: 1300 638 632</div>
    </div>
    <div class="dashboard">
        <div onclick="showReviews()">Customer Reviews</div>
        <div onclick="alert('Settings coming soon!')">Settings</div>
        <div onclick="alert('More Security Features Available!')">Security Features</div>
    </div>
    <div class="review-section" id="reviews">
        <h2>Customer Reviews</h2>
        <p>⭐⭐⭐⭐⭐ "Excellent security solutions!" - John D.</p>
        <p>⭐⭐⭐⭐⭐ "Reliable cameras with great night vision." - Sarah K.</p>
        <button onclick="hideReviews()">Close</button>
    </div>
    <script>
        function toggleMenu() {
            var menu = document.getElementById("menuContent");
            menu.style.display = menu.style.display === "block" ? "none" : "block";
        }
        function showReviews() {
            document.getElementById("reviews").style.display = "block";
        }
        function hideReviews() {
            document.getElementById("reviews").style.display = "none";
        }
        function showAbout() {
            alert("Our company is located in Chennai.");
        }
    </script>
</body>
</html>




