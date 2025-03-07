 <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ME MOBILES - Your Premium Mobile Store</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        :root {
            --primary: #4e54c8;
            --secondary: #8f94fb;
            --accent: #ff6b6b;
            --light: #f9f9f9;
            --dark: #333;
            --call: #e74c3c;
            --instagram: #C13584;
        }

        body {
            background: linear-gradient(45deg, var(--primary), var(--secondary));
            color: var(--dark);
            overflow-x: hidden;
        }

        /* Lighting effects */
        .light-effect {
            position: absolute;
            width: 150px;
            height: 150px;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.15);
            filter: blur(40px);
            z-index: -1;
            animation: float 6s ease-in-out infinite;
        }

        .light-1 {
            top: 20%;
            left: 5%;
            background: rgba(255, 107, 107, 0.2);
        }

        .light-2 {
            top: 50%;
            right: 10%;
            background: rgba(143, 148, 251, 0.2);
        }

        .light-3 {
            bottom: 10%;
            left: 30%;
            background: rgba(255, 196, 0, 0.2);
        }

        @keyframes float {
            0%, 100% { transform: translateY(0) scale(1); }
            50% { transform: translateY(-20px) scale(1.1); }
        }

        /* Header */
        header {
            background-color: rgba(0, 0, 0, 0.7);
            color: white;
            padding: 1rem;
            position: sticky;
            top: 0;
            z-index: 1000;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
        }

        .logo {
            display: flex;
            align-items: center;
        }

        .logo h1 {
            font-size: 2.5rem;
            margin-left: 10px;
            background: linear-gradient(to right, #ff6b6b, #8f94fb);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: color-change 5s infinite alternate;
            text-shadow: 0 0 10px rgba(255, 255, 255, 0.3);
        }

        .header-buttons {
            display: flex;
            gap: 1rem;
        }

        @keyframes color-change {
            0% { filter: hue-rotate(0deg); }
            100% { filter: hue-rotate(360deg); }
        }

        .dashboard-btn, .location-btn, .call-btn, .instagram-btn {
            background-color: var(--accent);
            color: white;
            border: none;
            padding: 0.5rem 1rem;
            border-radius: 5px;
            cursor: pointer;
            transition: all 0.3s ease;
            text-decoration: none;
            display: inline-block;
        }

        .dashboard-btn:hover, .location-btn:hover, .call-btn:hover, .instagram-btn:hover {
            background-color: #ff4f4f;
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(255, 107, 107, 0.4);
        }

        .location-btn {
            background-color: #25D366;
        }

        .location-btn:hover {
            background-color: #128C7E;
            box-shadow: 0 5px 15px rgba(37, 211, 102, 0.4);
        }

        .instagram-btn {
            background-color: var(--instagram);
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .instagram-btn:hover {
            background-color: #8a3ab9;
            box-shadow: 0 5px 15px rgba(193, 53, 132, 0.4);
        }

        .call-btn {
            background-color: #222;
            box-shadow: 0 0 10px rgba(231, 76, 60, 0.5);
            position: relative;
            overflow: hidden;
        }

        .call-btn:hover {
            background-color: #111;
            box-shadow: 0 0 20px rgba(231, 76, 60, 0.8);
        }

        .call-btn::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: rgba(231, 76, 60, 0.3);
            transform: rotate(45deg);
            z-index: 1;
            transition: all 0.5s ease;
            pointer-events: none;
        }

        .call-btn:hover::before {
            animation: shine 1.5s infinite;
        }

        /* Fixed Contact Buttons */
        .fixed-contact {
            position: fixed;
            bottom: 30px;
            right: 30px;
            display: flex;
            flex-direction: column;
            gap: 10px;
            z-index: 999;
        }

        .fixed-btn {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 24px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3);
            cursor: pointer;
            border: none;
            transition: all 0.3s ease;
        }

        .fixed-location {
            background-color: #25D366;
            color: white;
        }

        .fixed-call {
            background-color: #e74c3c;
            color: white;
        }

        .fixed-instagram {
            background-color: #C13584;
            color: white;
        }

        .fixed-btn:hover {
            transform: scale(1.1);
        }

        /* Instagram Icon */
        .instagram-icon {
            display: inline-block;
            width: 24px;
            height: 24px;
            background: radial-gradient(circle at 30% 107%, #fdf497 0%, #fdf497 5%, #fd5949 45%, #d6249f 60%, #285AEB 90%);
            border-radius: 7px;
            position: relative;
        }

        .instagram-icon::after {
            content: '';
            position: absolute;
            top: 5px;
            left: 5px;
            width: 14px;
            height: 14px;
            border: 2px solid white;
            border-radius: 5px;
        }

        .instagram-icon::before {
            content: '';
            position: absolute;
            top: 8px;
            left: 8px;
            width: 8px;
            height: 8px;
            border: 2px solid white;
            border-radius: 50%;
        }

        /* Quote Section */
        .quote-section {
            text-align: center;
            padding: 2rem;
            background-color: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            margin: 2rem 0;
            border-radius: 10px;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
        }

        .quote {
            font-style: italic;
            font-size: 1.2rem;
            color: white;
            text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.3);
            margin-bottom: 1rem;
        }

        /* Products */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 2rem;
        }

        .products {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }

        .product-card {
            background-color: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            position: relative;
        }

        .product-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 40px rgba(0, 0, 0, 0.2);
        }

        .product-img {
            width: 100%;
            height: 220px;
            object-fit: contain;
            background-color: #f9f9f9;
            padding: 1rem;
        }

        .product-details {
            padding: 1.5rem;
        }

        .product-title {
            font-size: 1.2rem;
            margin-bottom: 0.5rem;
            color: var(--dark);
        }

        .product-price {
            font-size: 1.3rem;
            font-weight: bold;
            color: var(--accent);
            margin-bottom: 1rem;
        }

        .product-description {
            color: #666;
            font-size: 0.9rem;
            margin-bottom: 1rem;
        }

        /* Rating */
        .rating {
            display: flex;
            margin-bottom: 1rem;
        }

        .stars {
            color: gold;
            font-size: 1.2rem;
            margin-right: 0.5rem;
        }

        .rating-count {
            color: #666;
            font-size: 0.9rem;
        }

        /* Buy Button */
        .buy-btn {
            background: linear-gradient(45deg, var(--primary), var(--secondary));
            color: white;
            border: none;
            padding: 0.8rem 1.5rem;
            border-radius: 30px;
            font-weight: bold;
            cursor: pointer;
            width: 100%;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(78, 84, 200, 0.3);
            position: relative;
            overflow: hidden;
        }

        .buy-btn:hover {
            background: linear-gradient(45deg, var(--secondary), var(--primary));
            transform: translateY(-2px);
            box-shadow: 0 8px 20px rgba(78, 84, 200, 0.5);
        }

        /* Button lighting effects */
        .buy-btn::before {
            content: "";
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: rgba(255, 255, 255, 0.2);
            transform: rotate(45deg);
            z-index: 1;
            transition: all 0.5s ease;
            pointer-events: none;
        }

        .buy-btn:hover::before {
            animation: shine 1.5s infinite;
        }

        .buy-btn::after {
            content: "";
            position: absolute;
            width: 10px;
            height: 10px;
            border-radius: 50%;
            background-color: rgba(255, 255, 255, 0.5);
            pointer-events: none;
            filter: blur(5px);
            z-index: 1;
        }

        .buy-btn .light-dot {
            position: absolute;
            width: 5px;
            height: 5px;
            border-radius: 50%;
            background-color: rgba(255, 255, 255, 0.8);
            filter: blur(2px);
            z-index: 1;
            pointer-events: none;
        }

        .buy-btn .light-dot:nth-child(1) {
            top: 20%;
            left: 10%;
            animation: pulse 2s infinite;
        }

        .buy-btn .light-dot:nth-child(2) {
            top: 30%;
            left: 80%;
            animation: pulse 3s infinite 0.5s;
        }

        .buy-btn .light-dot:nth-child(3) {
            top: 70%;
            left: 20%;
            animation: pulse 2.5s infinite 1s;
        }

        .buy-btn .light-dot:nth-child(4) {
            top: 60%;
            left: 70%;
            animation: pulse 3.5s infinite 1.5s;
        }

        @keyframes shine {
            0% {
                left: -100%;
                opacity: 0;
            }
            10% {
                left: -100%;
                opacity: 0.5;
            }
            50% {
                left: 100%;
                opacity: 0.3;
            }
            100% {
                left: 100%;
                opacity: 0;
            }
        }

        @keyframes pulse {
            0%, 100% {
                opacity: 0.3;
                transform: scale(1);
            }
            50% {
                opacity: 0.8;
                transform: scale(1.5);
            }
        }

        /* Reviews Section */
        .reviews-section {
            background-color: white;
            padding: 2rem;
            border-radius: 10px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            margin: 3rem 0;
        }

        .reviews-title {
            text-align: center;
            margin-bottom: 2rem;
            color: var(--primary);
        }

        .reviews-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 1.5rem;
        }

        .review-card {
            background: linear-gradient(45deg, #f5f7fa, #c3cfe2);
            padding: 1.5rem;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }

        .review-header {
            display: flex;
            align-items: center;
            margin-bottom: 1rem;
        }

        .reviewer-img {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            margin-right: 1rem;
            background-color: #ddd;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
        }

        .reviewer-info {
            flex: 1;
        }

        .reviewer-name {
            font-weight: bold;
            color: var(--dark);
        }

        .review-date {
            font-size: 0.8rem;
            color: #777;
        }

        .review-text {
            font-size: 0.9rem;
            color: #555;
            line-height: 1.5;
        }

        .add-review {
            background-color: #f9f9f9;
            padding: 1.5rem;
            border-radius: 10px;
            margin-top: 2rem;
        }

        .add-review-title {
            font-size: 1.2rem;
            margin-bottom: 1rem;
            color: var(--primary);
        }

        .review-form {
            display: grid;
            gap: 1rem;
        }

        .review-form-group {
            display: grid;
            gap: 0.5rem;
        }

        .review-input, .review-textarea {
            padding: 0.8rem;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-size: 0.9rem;
        }

        .review-textarea {
            resize: vertical;
            min-height: 100px;
        }

        .review-submit {
            background: linear-gradient(45deg, var(--primary), var(--secondary));
            color: white;
            border: none;
            padding: 0.8rem 1.5rem;
            border-radius: 5px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .review-submit:hover {
            background: linear-gradient(45deg, var(--secondary), var(--primary));
            transform: translateY(-2px);
        }

        /* WhatsApp Contact Form */
        .whatsapp-form {
            background: white;
            padding: 2rem;
            border-radius: 10px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            margin: 3rem 0;
        }

        .whatsapp-form-title {
            text-align: center;
            margin-bottom: 1.5rem;
            color: var(--primary);
            font-size: 1.8rem;
        }

        .whatsapp-form-subtitle {
            text-align: center;
            margin-bottom: 2rem;
            color: #666;
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 500;
            color: #333;
        }

        .form-control {
            width: 100%;
            padding: 1rem;
            border: 1px solid #ddd;
            border-radius: 8px;
            font-size: 1rem;
            transition: all 0.3s ease;
        }

        .form-control:focus {
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(78, 84, 200, 0.1);
            outline: none;
        }

        .whatsapp-submit {
            background: linear-gradient(45deg, #25D366, #128C7E);
            color: white;
            border: none;
            padding: 1rem;
            border-radius: 8px;
            font-weight: bold;
            font-size: 1.1rem;
            cursor: pointer;
            width: 100%;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 0.5rem;
        }

        .whatsapp-submit:hover {
            background: linear-gradient(45deg, #128C7E, #075E54);
            transform: translateY(-2px);
            box-shadow: 0 8px 20px rgba(37, 211, 102, 0.3);
        }

        .whatsapp-icon {
            font-size: 1.5rem;
        }

        /* Footer */
        footer {
            background-color: rgba(0, 0, 0, 0.7);
            color: white;
            text-align: center;
            padding: 2rem;
            margin-top: 3rem;
        }

        .social-icons {
            display: flex;
            justify-content: center;
            gap: 1.5rem;
            margin: 1.5rem 0;
        }

        .social-icon {
            color: white;
            font-size: 1.8rem;
            transition: transform 0.3s ease, color 0.3s ease;
            text-decoration: none;
        }

        .social-icon:hover {
            transform: translateY(-5px);
        }

        .social-icon.instagram:hover {
            color: #C13584;
        }

        /* Dashboard Modal */
        .modal {
            display: none;
            position: fixed;
            z-index: 1100;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            overflow: auto;
            background-color: rgba(0, 0, 0, 0.5);
        }

        .modal-content {
            background-color: white;
            margin: 10% auto;
            padding: 2rem;
            border-radius: 10px;
            width: 80%;
            max-width: 800px;
            animation: slideIn 0.3s ease;
        }

        @keyframes slideIn {
            from { transform: translateY(-50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        .close {
            color: #aaa;
            float: right;
            font-size: 28px;
            font-weight: bold;
            cursor: pointer;
        }

        .close:hover {
            color: var(--dark);
        }

        .dashboard-stats {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 1rem;
            margin-top: 1.5rem;
        }

        .stat-card {
            background: linear-gradient(45deg, #f1f1f1, #ffffff);
            padding: 1.5rem;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            text-align: center;
        }

        .stat-number {
            font-size: 2rem;
            font-weight: bold;
            color: var(--primary);
            margin-bottom: 0.5rem;
        }

        .stat-label {
            color: #666;
            font-size: 0.9rem;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .container {
                padding: 1rem;
            }
            
            .products {
                grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
                gap: 1rem;
            }
            
            .logo h1 {
                font-size: 2rem;
            }

            .header-buttons {
                gap: 0.5rem;
            }

            .dashboard-btn, .location-btn, .call-btn, .instagram-btn {
                padding: 0.4rem 0.7rem;
                font-size: 0.9rem;
            }

            .reviews-container {
                grid-template-columns: 1fr;
            }

            .fixed-contact {
                bottom: 20px;
                right: 20px;
            }

            .fixed-btn {
                width: 50px;
                height: 50px;
                font-size: 20px;
            }
        }
    </style>
</head>
<body>
    <!-- Lighting effects -->
    <div class="light-effect light-1"></div>
    <div class="light-effect light-2"></div>
    <div class="light-effect light-3"></div>

    <!-- Header -->
    <header>
        <div class="logo">
            <h1>ME MOBILES</h1>
        </div>
        <div class="header-buttons">
            <a href="tel:8489061134" class="call-btn">📞 Call Now</a>
            <a href="https://maps.app.goo.gl/vb5tbLS44LTodcHE9?g_st=ic" class="location-btn" target="_blank">📍 Location</a>
            <a href="https://www.instagram.com/me_mobiles_krishnagiri?igsh=NWF3cmNwdDY4ZTJl" class="instagram-btn" target="_blank">
                <div class="instagram-icon"></div>
            </a>
            <button class="dashboard-btn" onclick="openDashboard()">Dashboard</button>
        </div>
    </header>

    <!-- Fixed Contact Buttons -->
    <div class="fixed-contact">
        <a href="tel:8489061134" class="fixed-btn fixed-call">📞</a>
        <a href="https://maps.app.goo.gl/vb5tbLS44LTodcHE9?g_st=ic" target="_blank" class="fixed-btn fixed-location">📍</a>
        <a href="https://www.instagram.com/me_mobiles_krishnagiri?igsh=NWF3cmNwdDY4ZTJl" target="_blank" class="fixed-btn fixed-instagram">
            <div class="instagram-icon"></div>
        </a>
    </div>

    <!-- Quote Section -->
    <div class="container">
        <div class="quote-section">
            <p class="quote">"The future of mobile technology is not just about connecting devices, but connecting lives."</p>
            <p class="quote">"Innovation in your hands, excellence in every pixel."</p>
            <p class="quote">"Stay connected to what matters most with ME MOBILES."</p>
        </div>
    </div>

    <!-- Main Content -->
    <div class="container">
        <h2 style="text-align: center; color: white; margin-bottom: 1rem;">Featured Products</h2>
        
        <!-- Products Grid -->
        <div class="products">
            <!-- Product 1 -->
            <div class="product-card">
                <img src="/api/placeholder/400/320" alt="Smartphone Model X" class="product-img">
                <div class="product-details">
                    <h3 class="product-title">ME Ultra Pro 13</h3>
                    <div class="rating">
                        <div class="stars">★★★★★</div>
                        <span class="rating-count">(128)</span>
                    </div>
                    <p class="product-price">₹74,999</p>
                    <p class="product-description">Flagship smartphone with 6.7" AMOLED display, 108MP camera system, and 5G connectivity.</p>
                    <button class="buy-btn" onclick="sendWhatsAppOrder('ME Ultra Pro 13', '₹74,999')">
                        Buy Now
                        <span class="light-dot"></span>
                        <span class="light-dot"></span>
                        <span class="light-dot"></span>
                        <span class="light-dot"></span>
                    </button>
                </div>
            </div>

            <!-- Product 2 -->
            <div class="product-card">
                <img src="/api/placeholder/400/320" alt="Smartphone Model Y" class="product-img">
                <div class="product-details">
                    <h3 class="product-title">ME Lite 8</h3>
                    <div class="rating">
                        <div class="stars">★★★★☆</div>
                        <span class="rating-count">(94)</span>
                    </div>
                    <p class="product-price">₹42,999</p>
                    <p class="product-description">Mid-range powerhouse with 6.4" display, 64MP quad camera, and all-day battery life.</p>
                    <button class="buy-btn" onclick="sendWhatsAppOrder('ME Lite 8', '₹42,999')">
                        Buy Now
                        <span class="light-dot"></span>
                        <span class="light-dot"></span>
                        <span class="light-dot"></span>
                        <span class="light-dot"></span>
                    </button>
                </div>
            </div>

            <!-- Product 3 -->
            <div class="product-card">
                <img src="/api/placeholder/400/320" alt="Smartphone Model Z" class="product-img">
                <div class="product-details">
                    <h3 class="product-title">ME Fold X</h3>
                    <div class="rating">
                        <div class="stars">★★★★★</div>
                        <span class="rating-count">(56)</span>
                    </div>
                    <p class="product-price">₹1,09,999</p>
                    <p class="product-description">Revolutionary foldable smartphone with dual 7.6" and 6.3" displays, multitasking capabilities.</p>
                    <button class="buy-btn" onclick="sendWhatsAppOrder('ME Fold X', '₹1,09,999')">
                        Buy Now
                        <span class="light-dot"></span>
                        <span class="light-dot"></span>
                        <span class="light-dot"></span>
                        <span class="light-dot"></span>
                    </button>
                </div>
            </div>

            <!-- Product 4 -->
            <div class="product-card">
                <img src="/api/placeholder/400/320" alt="Smartphone Budget" class="product-img">
                <div class="product-details">
                    <h3 class="product-title">ME Essential</h3>
                    <div class="rating">
                        <div class="stars">★★★★☆</div>
                        <span class="rating-count">(212)</span>
                    </div>
                    <p class="product-price">₹24,999</p>
                    <p class="product-description">Budget-friendly with flagship features, 6.2" display, 48MP camera, and fast charging.</p>
                    <button class="buy-btn" onclick="sendWhatsAppOrder('ME Essential', '₹24,999')">
                        Buy Now
                        <span class="light-dot"></span>
                        <span class="light-dot"></span>
                        <span class="light-dot"></span>
                        <span class="light-dot"></span>
                    </button>
                </div>
            </div>
        </div>

        <!-- Reviews Section -->
        <div class="reviews-section">
            <h2 class="reviews-title">Customer Reviews</h2>
            <div class="reviews-container">
                <!-- Review 1 -->
                <div class="review-card">
                    <div class="review-header">
                        <div class="reviewer-img">👨</div>
                        <div class="reviewer-info">
                            <div class="reviewer-name">Rajesh Kumar</div>
                            <div class="review-date">February 28, 2025</div>
                            <div class="stars">★★★★★</div>
                        </div>
                    </div>
                    <div class="review-text">
                        Just purchased the ME Ultra Pro 13
