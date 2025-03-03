 <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GV Safe Site Construction Cameras</title>

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
            transition: background 0.5s ease-in-out;
            line-height: 1.5em;
        }

        /* Navbar */
        header {
            padding: 25px;
            background: rgba(0, 0, 0, 0.8);
            font-family: 'Orbitron', sans-serif;
            font-size: 28px;
            letter-spacing: 3px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding-left: 30px;
            padding-right: 30px;
        }

        .logo {
            font-size: 26px;
            font-weight: bold;
        }

        .top-right-menu {
            cursor: pointer;
            font-size: 26px;
            background: #ffcc00;
            padding: 10px 15px;
            border-radius: 8px;
            color: black;
            box-shadow: 0 0 15px white;
            transition: 0.3s;
        }

        .top-right-menu:hover {
            background: #ff9900;
        }

        .menu-content {
            display: none;
            position: absolute;
            right: 30px;
            top: 65px;
            background: rgba(0, 0, 0, 0.9);
            padding: 15px;
            border-radius: 8px;
            box-shadow: 0 0 15px white;
        }

        .menu-content a {
            display: block;
            color: white;
            text-decoration: none;
            padding: 10px;
            transition: 0.3s;
        }

        .menu-content a:hover {
            background: #ffcc00;
            color: black;
        }

        /* Main Content */
        .container {
            padding: 60px;
            background: url('https://source.unsplash.com/1600x900/?cctv,security') no-repeat center center/cover;
            min-height: 85vh;
        }

        .features {
            padding: 30px;
            background: rgba(0, 0, 0, 0.5);
            margin-top: 30px;
        }

        /* Buttons */
        .bottom-dashboard {
            padding: 30px;
            background: black;
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 20px;
            box-shadow: 0 0 20px white;
            margin-top: 50px;
            width: 100%;
        }

        .bottom-dashboard div {
            background: #444;
            padding: 25px;
            width: 30%;
            border-radius: 12px;
            cursor: pointer;
            transition: 0.3s;
            box-shadow: 0 0 20px white;
            font-size: 18px;
            font-weight: bold;
            text-align: center;
        }

        .bottom-dashboard div:hover {
            box-shadow: 0 0 40px white;
            transform: scale(1.05);
        }

        /* Booking Form */
        .booking-section {
            background: rgba(0, 0, 0, 0.8);
            padding: 30px;
            width: 60%;
            margin: 40px auto;
            border-radius: 10px;
            box-shadow: 0 0 20px white;
        }

        .booking-section h2 {
            margin-bottom: 20px;
        }

        .booking-form input, 
        .booking-form select, 
        .booking-form button {
            width: 100%;
            padding: 12px;
            margin-top: 10px;
            border-radius: 6px;
            border: none;
            font-size: 16px;
        }

        .booking-form button {
            background: #ffcc00;
            color: black;
            font-weight: bold;
            cursor: pointer;
            transition: 0.3s;
        }

        .booking-form button:hover {
            background: #ff9900;
        }

        /* Dark Mode */
        .dark-mode-toggle {
            position: fixed;
            bottom: 30px;
            right: 30px;
            background: #ffcc00;
            padding: 15px;
            border-radius: 8px;
            cursor: pointer;
            font-weight: bold;
            font-size: 18px;
            color: black;
            box-shadow: 0 0 15px white;
            transition: 0.3s;
        }

        .dark-mode-toggle:hover {
            background: #ff9900;
        }

        @media (max-width: 768px) {
            .bottom-dashboard div {
                width: 80%;
            }

            .booking-section {
                width: 90%;
            }
        }
    </style>
</head>
<body>

    <header>
        <div class="logo">GV Safe Site</div>
        <div class="top-right-menu" onclick="toggleMenu()">☰</div>
        <div class="menu-content" id="menuContent">
            <a href="#">About Us</a>
            <a href="#contact">Contact Us</a>
            <a href="mailto:surya.murali109@gmail.com">Email</a>
            <a href="https://wa.me/9342792571">WhatsApp</a>
        </div>
    </header>

    <div class="container">
        <h2>📡 24/7 Surveillance | 🤖 AI-powered Monitoring | 📷 High-Resolution CCTV</h2>
        <p>🔒 Secure your site with the best-in-class CCTV solutions, ensuring safety and real-time monitoring.</p>
        <div class="features">
            <p>✔ Live HD Streaming &nbsp;&nbsp;|&nbsp;&nbsp; ✔ Motion Detection &nbsp;&nbsp;|&nbsp;&nbsp; ✔ Cloud Storage</p>
        </div>
    </div>

    <div class="bottom-dashboard">
        <div onclick="alert('Customer reviews coming soon!')">🌟 Customer Reviews</div>
        <div onclick="alert('⚙️ Settings coming soon!')">⚙️ Settings</div>
        <div onclick="alert('Security features coming soon!')">🔐 Security Features</div>
    </div>

    <!-- Booking Form -->
    <div class="booking-section">
        <h2>📋 Book a CCTV Camera</h2>
        <form class="booking-form">
            <input type="text" placeholder="Your Name" required>
            <input type="tel" placeholder="Contact Number" required>
            <select>
                <option>Camera Type</option>
                <option>HD CCTV</option>
                <option>Wireless CCTV</option>
                <option>AI-powered CCTV</option>
            </select>
            <input type="date" required>
            <input type="text" placeholder="Installation Address" required>
            <button type="submit">Book Now</button>
        </form>
    </div>

</body>
</html>
