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
        }

        .container {
            padding: 50px;
            background: url('https://source.unsplash.com/1600x900/?cctv,security') no-repeat center center/cover;
            min-height: 60vh;
        }

        /* CCTV Images Section */
        .cctv-gallery {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 20px;
            margin: 30px auto;
            width: 80%;
        }

        .cctv-gallery img {
            width: 30%;
            height: auto;
            border-radius: 10px;
            box-shadow: 0 0 15px white;
            transition: 0.3s;
        }

        .cctv-gallery img:hover {
            transform: scale(1.05);
        }

        /* Booking Section */
        .booking-section {
            background: rgba(0, 0, 0, 0.9);
            padding: 50px;
            width: 60%;
            margin: 30px auto;
            border-radius: 10px;
            box-shadow: 0 0 20px white;
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
        }

        /* Footer */
        .footer {
            padding: 20px;
            background: black;
            color: white;
            text-align: center;
            box-shadow: 0 0 15px white;
            margin-top: 20px;
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .container {
                padding: 30px;
                min-height: 50vh;
            }

            .cctv-gallery {
                width: 100%;
                flex-direction: column;
                align-items: center;
            }

            .cctv-gallery img {
                width: 80%;
            }

            .booking-section {
                width: 90%;
                padding: 30px;
            }
        }
    </style>
</head>
<body>

    <header>
        <h1>📷 GV Safe Site Construction Cameras 📷</h1>
    </header>

    <div class="container">
        <h2>📡 24/7 Surveillance | 🤖 AI-powered Monitoring | 📷 High-Resolution CCTV</h2>
        <p>🔒 Secure your site with the best-in-class CCTV solutions, ensuring safety and real-time monitoring.</p>
    </div>

    <!-- CCTV Image Gallery -->
    <div class="cctv-gallery">
        <img src="https://source.unsplash.com/400x300/?cctv,camera" alt="CCTV Camera 1">
        <img src="https://source.unsplash.com/400x300/?security,camera" alt="CCTV Camera 2">
        <img src="https://source.unsplash.com/400x300/?surveillance,camera" alt="CCTV Camera 3">
    </div>

    <!-- Booking Form -->
    <div class="booking-section">
        <h2>📅 Book Your CCTV Now</h2>
        <div class="booking-form">
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

    <!-- Footer Section -->
    <div class="footer">
        <p>📞 Contact Us: 1300 638 632 | ✉ Email: <a href="mailto:surya.murali109@gmail.com">surya.murali109@gmail.com</a> | 📱 WhatsApp: <a href="https://wa.me/9342792571">9342792571</a></p>
        <p>© 2025 GV Safe Site Construction Cameras. All Rights Reserved.</p>
    </div>

</body>
</html>
