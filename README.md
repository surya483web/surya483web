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
            background: rgba(0, 0, 0, 0.7);
            font-family: 'Orbitron', sans-serif;
            font-size: 28px;
            letter-spacing: 3px;
            position: relative;
        }

        .top-right-menu {
            position: absolute;
            top: 15px;
            right: 20px;
            cursor: pointer;
            font-size: 24px;
            background: #ffcc00;
            padding: 8px 15px;
            border-radius: 8px;
            color: black;
            box-shadow: 0 0 15px white;
            transition: 0.3s;
        }

        .top-right-menu:hover {
            background: #ff9900;
        }

        .container {
            display: flex;
            justify-content: space-around;
            align-items: center;
            padding: 50px;
            background: url('https://source.unsplash.com/1600x900/?cctv,security') no-repeat center center/cover;
            min-height: 80vh;
        }

        .content {
            width: 45%;
            text-align: left;
        }

        .features {
            background: rgba(0, 0, 0, 0.5);
            padding: 15px;
            display: inline-block;
            border-radius: 5px;
        }

        .booking-form {
            background: rgba(255, 255, 255, 0.1);
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 0 20px white;
            width: 45%;
            text-align: left;
        }

        .booking-form h2 {
            margin-bottom: 15px;
            font-size: 24px;
            text-align: center;
        }

        .booking-form input, 
        .booking-form select, 
        .booking-form textarea {
            width: 100%;
            padding: 10px;
            margin: 8px 0;
            border: none;
            border-radius: 5px;
            font-size: 16px;
        }

        .booking-form button {
            background: #ffcc00;
            color: black;
            font-size: 18px;
            padding: 10px;
            border: none;
            cursor: pointer;
            width: 100%;
            border-radius: 5px;
            font-weight: bold;
            transition: 0.3s;
        }

        .booking-form button:hover {
            background: #ff9900;
        }

        .bottom-dashboard {
            display: flex;
            justify-content: space-around;
            padding: 20px;
            background: black;
            box-shadow: 0 0 20px white;
        }

        .bottom-dashboard div {
            background: #444;
            padding: 15px;
            width: 30%;
            border-radius: 10px;
            cursor: pointer;
            transition: 0.3s;
            box-shadow: 0 0 20px white;
            font-size: 16px;
            font-weight: bold;
        }

        .bottom-dashboard div:hover {
            box-shadow: 0 0 40px white;
            transform: scale(1.05);
        }

        @media (max-width: 768px) {
            .container {
                flex-direction: column;
            }

            .content, .booking-form {
                width: 90%;
                text-align: center;
            }

            .bottom-dashboard div {
                width: 80%;
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
        <div class="content">
            <h2>📡 24/7 Surveillance | 🤖 AI-powered Monitoring | 📷 High-Resolution CCTV</h2>
            <p>🔒 Secure your site with the best-in-class CCTV solutions, ensuring safety and real-time monitoring.</p>
            <div class="features">
                <p>✔ Live HD Streaming &nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp; ✔ Motion Detection &nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp; ✔ Cloud Storage</p>
            </div>
        </div>

        <div class="booking-form">
            <h2>📅 Book Your CCTV Now</h2>
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

    <script>
        function submitBooking() {
            let name = document.getElementById("name").value;
            let phone = document.getElementById("phone").value;
            let cameraType = document.getElementById("cameraType").value;
            let installationDate = document.getElementById("installationDate").value;
            let address = document.getElementById("address").value;

            let message = `Booking Details:\n\nName: ${name}\nPhone: ${phone}\nCamera Type: ${cameraType}\nInstallation Date: ${installationDate}\nAddress: ${address}`;

            // Send Email
            let mailtoLink = `mailto:surya.murali109@gmail.com?subject=CCTV Booking Request&body=${encodeURIComponent(message)}`;
            window.location.href = mailtoLink;

            // Send WhatsApp Message
            let whatsappLink = `https://wa.me/9342792571?text=${encodeURIComponent(message)}`;
            window.open(whatsappLink, "_blank");
        }
    </script>

</body>
</html>
