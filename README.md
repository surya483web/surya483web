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
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }

        .features {
            padding: 30px;
            background: rgba(0, 0, 0, 0.5);
            margin-top: 30px;
            width: 60%;
            border-radius: 10px;
        }

        /* Booking Form Centered */
        .booking-section {
            background: rgba(0, 0, 0, 0.8);
            padding: 30px;
            width: 50%;
            margin: auto;
            border-radius: 10px;
            box-shadow: 0 0 20px white;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            text-align: center;
        }

        .booking-section h2 {
            margin-bottom: 20px;
        }

        .booking-form input, 
        .booking-form select, 
        .booking-form button {
            width: 90%;
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

        /* Responsive Design */
        @media (max-width: 768px) {
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

    <!-- Booking Form (Centered) -->
    <div class="booking-section">
        <h2>📋 Book a CCTV Camera</h2>
        <form class="booking-form" action="https://formspree.io/f/YOUR_FORM_ID" method="POST" onsubmit="sendWhatsAppMessage(event)">
            <input type="text" id="name" name="name" placeholder="Your Name" required>
            <input type="tel" id="contact" name="contact" placeholder="Contact Number" required>
            <select id="camera" name="camera_type">
                <option>Camera Type</option>
                <option>HD CCTV</option>
                <option>Wireless CCTV</option>
                <option>AI-powered CCTV</option>
            </select>
            <input type="date" id="date" name="installation_date" required>
            <input type="text" id="address" name="address" placeholder="Installation Address" required>
            <button type="submit">Book Now</button>
        </form>
    </div>

    <script>
        function sendWhatsAppMessage(event) {
            event.preventDefault(); // Prevent form from submitting immediately

            let name = document.getElementById("name").value;
            let contact = document.getElementById("contact").value;
            let camera = document.getElementById("camera").value;
            let date = document.getElementById("date").value;
            let address = document.getElementById("address").value;

            let message = `Booking Details:
            Name: ${name}
            Contact: ${contact}
            Camera Type: ${camera}
            Installation Date: ${date}
            Address: ${address}`;

            let whatsappURL = `https://wa.me/9342792571?text=${encodeURIComponent(message)}`;
            window.open(whatsappURL, "_blank");

            // Allow Formspree to send email after WhatsApp redirection
            setTimeout(() => {
                event.target.submit();
            }, 1000);
        }
    </script>

</body>
</html>
