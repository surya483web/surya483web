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

        /* Image Gallery Section */
        .image-gallery {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 20px;
            margin: 40px auto;
            width: 80%;
        }

        .gallery-item {
            flex: 0 0 calc(33.33% - 20px);
            max-width: calc(33.33% - 20px);
            overflow: hidden;
            border-radius: 10px;
            box-shadow: 0 0 15px rgba(255, 255, 255, 0.7);
            transition: transform 0.3s ease;
            position: relative;
        }

        .gallery-item:hover {
            transform: scale(1.05);
        }

        .gallery-item img {
            width: 100%;
            height: 250px;
            object-fit: cover;
            display: block;
        }

        .gallery-caption {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            background: rgba(0, 0, 0, 0.7);
            padding: 10px;
            font-size: 16px;
            font-weight: bold;
        }

        /* Benefits Section */
        .benefits-section {
            padding: 40px;
            background: rgba(0, 0, 0, 0.7);
            margin: 20px auto;
            width: 80%;
            border-radius: 10px;
            box-shadow: 0 0 15px white;
        }

        .benefits-section h2 {
            margin-bottom: 15px;
            font-size: 26px;
            text-shadow: 2px 2px 10px white;
        }

        .benefits-section ul {
            list-style: none;
            padding: 0;
        }

        .benefits-section li {
            font-size: 18px;
            margin: 10px 0;
        }

        /* Booking Section */
        .booking-section {
            background: rgba(0, 0, 0, 0.9);
            padding: 50px;
            width: 60%;
            margin: 50px auto;
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
                padding: 40px;
                min-height: 50vh;
            }

            .booking-section {
                width: 90%;
                padding: 30px;
            }

            .benefits-section {
                width: 90%;
                padding: 30px;
            }
            
            .image-gallery {
                width: 90%;
            }
            
            .gallery-item {
                flex: 0 0 100%;
                max-width: 100%;
                margin-bottom: 20px;
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

    <!-- CCTV Images Gallery -->
    <h2 style="margin-top: 40px; text-shadow: 2px 2px 10px white;">Our Advanced CCTV Solutions</h2>
    <div class="image-gallery">
        <div class="gallery-item">
            <img src="/api/placeholder/400/320" alt="Construction Site CCTV Camera" />
            <div class="gallery-caption">Construction Site Surveillance</div>
        </div>
        <div class="gallery-item">
            <img src="/api/placeholder/400/320" alt="Night Vision CCTV Camera" />
            <div class="gallery-caption">Night Vision Monitoring</div>
        </div>
        <div class="gallery-item">
            <img src="/api/placeholder/400/320" alt="AI-Powered CCTV System" />
            <div class="gallery-caption">AI-Powered Analytics</div>
        </div>
    </div>

    <!-- Benefits Section -->
    <div class="benefits-section">
        <h2>🚀 Why Choose GV Safe Site Cameras?</h2>
        <ul>
            <li>✔ 24/7 Real-Time Monitoring</li>
            <li>✔ AI-Powered Motion Detection</li>
            <li>✔ High-Resolution Footage</li>
            <li>✔ Secure Cloud Storage</li>
            <li>✔ Professional Installation</li>
            <li>✔ Affordable Pricing & Reliable Support</li>
        </ul>
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
