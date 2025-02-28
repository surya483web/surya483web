 <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Profile Card</title>
    <style>
        /* Reset body margin and padding */
        body {
            margin: 0;
            padding: 0;
            font-family: 'Arial', sans-serif;
            background-color: #f0f0f0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        .card {
            background-color: white;
            width: 300px;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            overflow: hidden;
            text-align: center;
            transition: all 0.3s ease;
        }

        /* Profile image */
        .card img {
            width: 100%;
            height: 200px;
            object-fit: cover;
        }

        /* Card content */
        .card-content {
            padding: 20px;
        }

        .card-content h2 {
            margin: 10px 0;
            font-size: 22px;
            color: #333;
        }

        .card-content p {
            font-size: 16px;
            color: #777;
            margin-bottom: 20px;
        }

        .card-content .social-icons {
            display: flex;
            justify-content: center;
            gap: 15px;
        }

        .card-content .social-icons a {
            text-decoration: none;
            color: #333;
            font-size: 20px;
        }

        /* Hover effect on the card */
        .card:hover {
            transform: scale(1.05);
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.1);
        }

    </style>
</head>
<body>

    <div class="card">
        <img src="https://via.placeholder.com/300x200" alt="Profile Image">
        <div class="card-content">
            <h2>John Doe</h2>
            <p>Web Developer | Designer</p>
            <p>I am a passionate developer with experience in building beautiful and functional websites. I love creating web applications and learning new technologies.</p>

            <!-- Social Icons -->
            <div class="social-icons">
                <a href="https://facebook.com" target="_blank">FB</a>
                <a href="https://twitter.com" target="_blank">TW</a>
                <a href="https://linkedin.com" target="_blank">IN</a>
            </div>
        </div>
    </div>

</body>
</html>

