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
            border: 5px solid white;
            box-shadow: 0 0 20px white;
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
            box-shadow: 0 0 20px white;
        }
        .dashboard div:hover {
            box-shadow: 0 0 40px white;
        }
        .review-section, .security-section {
            display: none;
            padding: 20px;
            background: #333;
            border-radius: 10px;
            box-shadow: 0 0 20px white;
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 60%;
            height: auto;
            text-align: center;
        }
        .security-section {
            display: none;
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: #222;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 20px white;
            width: 60%;
            text-align: center;
        }
        .close-btn {
            position: absolute;
            top: 10px;
            right: 15px;
            font-size: 20px;
            cursor: pointer;
            color: white;
            background: red;
            padding: 5px;
            border-radius: 50%;
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
        <div onclick="showSecurityFeatures()">Security Features</div>
    </div>
    <div class="review-section" id="reviews">
        <h2>Customer Reviews</h2>
        <p>⭐⭐⭐⭐⭐ "Excellent security solutions!" - John D.</p>
        <p>⭐⭐⭐⭐⭐ "Reliable cameras with great night vision." - Sarah K.</p>
        <button onclick="hideReviews()">Close</button>
    </div>
    <div class="security-section" id="securityFeatures">
        <span class="close-btn" onclick="hideSecurityFeatures()">✖</span>
        <h2>Security Features</h2>
        <p>✔ AI-Powered Motion Detection</p>
        <p>✔ Night Vision Technology</p>
        <p>✔ Cloud-Enabled Storage</p>
        <p>✔ 360-Degree Monitoring</p>
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
        function showSecurityFeatures() {
            document.getElementById("securityFeatures").style.display = "block";
        }
        function hideSecurityFeatures() {
            document.getElementById("securityFeatures").style.display = "none";
        }
    </script>
</body>
</html>



