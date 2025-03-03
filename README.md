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
        }

        header {
            padding: 20px;
            background: rgba(0, 0, 0, 0.8);
            font-family: 'Orbitron', sans-serif;
            font-size: 28px;
            letter-spacing: 3px;
            position: relative;
            text-shadow: 2px 2px 10px rgba(255, 255, 255, 0.5);
        }

        .top-right-menu {
            position: absolute;
            top: 15px;
            right: 20px;
            cursor: pointer;
            font-size: 24px;
            background: #ffcc00;
            padding: 10px 15px;
            border-radius: 8px;
            color: black;
            box-shadow: 0 0 15px white;
            transition: 0.3s ease-in-out;
        }

        .top-right-menu:hover {
            background: #ff9900;
            transform: scale(1.1);
        }

        .container {
            padding: 60px;
            background: url('https://source.unsplash.com/1600x900/?cctv,security') no-repeat center center/cover;
            min-height: 50vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            border-radius: 10px;
            box-shadow: 0 0 20px white;
        }

        .features {
            padding: 25px;
            background: rgba(0, 0, 0, 0.6);
            margin-top: 20px;
            border-radius: 10px;
            box-shadow: 0 0 15px white;
        }

        .bottom-dashboard {
            padding: 25px;
            background: black;
            display: flex;
            justify-content: space-around;
            flex-wrap: wrap;
            box-shadow: 0 0 20px white;
            width: 100%;
            border-radius: 10px;
        }

        .bottom-dashboard div {
            background: #444;
            padding: 25px;
            width: 30%;
            margin: 10px;
            border-radius: 12px;
            cursor: pointer;
            transition: 0.3s;
            box-shadow: 0 0 20px white;
            font-size: 18px;
            font-weight: bold;
        }

        .bottom-dashboard div:hover {
            box-shadow: 0 0 40px white;
            transform: scale(1.05);
            background: #555;
        }

        /* Booking Form - Centered & User-Friendly */
        .booking-section {
            background: rgba(0, 0, 0, 0.9);
            padding: 50px;
            width: 60%;
            text-align: center;
            box-shadow: 0 0 20px white;
            margin: 50px auto;
            border-radius: 10px;
            transition: 0.3s ease-in-out;
        }

        .booking-form {
            background: rgba(255, 255, 255, 0.1);
            padding: 35px;
            border-radius: 10px;
            box-shadow: 0 0 20px white;
            width: 100%;
        }

        .booking-form h2 {
            margin-bottom: 20px;
            font-size: 26px;
            text-shadow: 2px 2px 10px white;
        }

        .booking-form input, 
        .booking-form select, 
        .booking-form textarea {
            width: 100%;
            padding: 12px;
            margin: 12px 0;
            border: none;
            border-radius: 5px;
            font-size: 18px;
            box-shadow: 0 0 10px white;
        }

        .booking-form button {
            background: #ffcc00;
            color: black;
            font-size: 20px;
            padding: 14px;
            border: none;
            cursor: pointer;
            width: 100%;
            border-radius: 5px;
            font-weight: bold;
            transition: 0.3s;
            box-shadow: 0 0 15px white;
        }

        .booking-form button:hover {
            background: #ff9900;
            transform: scale(1.05);
        }

        @media (max-width: 768px) {
            .booking-section {
                width: 90%;
            }

            .bottom-dashboard div {
                width: 80%;
            }

            .top-right-menu {
                font-size: 20px;
                padding: 8px 12px;
            }
        }
    </style>
</head>
<body>

    <header>
        <h1>📷 GV Safe Site Construction Cameras 📷</h1>
        <div class="top-right-menu" onclick="toggleMenu()">☰</div>
    </header>

    <div class="container">
        <h2>📡 24/7 Surveillance | 🤖 AI-powered Monitoring | 📷 High-Resolution CCTV</h2>
        <p>🔒 Secure your site with the best-in-class CCTV solutions, ensuring safety and real-time monitoring.</p>

        <div class="features">
            <p>✔ Live HD Streaming &nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp; ✔ Motion Detection &nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp; ✔ Cloud Storage</p>
        </div>
    </div>

    <!-- Booking Form in the Middle -->
    <div class="booking-section">
        <h2>📅 Book Your CCTV Now</h2>
        <div class="booking-form">
            <h2>Secure Your Site Today</h2>
            <form id="bookingForm">
                <input type="text" id="name" placeholder="Your Name" required>
                <input type="tel" id="phone" placeholder="Your Contact Number" required>
                <select id="cameraType">
                    <option value="HD Camera">HD Camera</option>
                    <option value="Night Vision Camera">Night Vision Camera</option>
                    <option value="AI-Powered Camera">AI-Powered Camera</option>
                </select>
                <input type="date" id="installationDate" required>
                <textarea id="address" placeholder="Installation Address" rows="4" required></textarea>
                <button type="button" onclick="submitBooking()">📩 Book Now</button>
            </form>
        </div>
    </div>

    <div class="bottom-dashboard">
        <div onclick="showReviews()">🌟 Customer Reviews</div>
        <div onclick="alert('⚙️ Settings coming soon!')">⚙️ Settings</div>
        <div onclick="showSecurityFeatures()">🔐 Security Features</div>
    </div>

</body>
</html>
