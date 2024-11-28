<h1>|WELCOME TO MY WEBSITE|</h1><br>
<hr>
<a href="https://www.youtube.com/">CLICK HERE YO GO "YOUTUBE" </a>
<img src="c:\Users\SURYA\Downloads\yt.htm" alt="">
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Simple Website</title>
    <style>
        /* General Reset */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: Arial, sans-serif;
            line-height: 1.6;
        }

        /* Navbar Styling */
        nav {
            background-color: #333;
            padding: 10px;
        }

        nav ul {
            list-style-type: none;
            display: flex;
            justify-content: center;
        }

        nav ul li {
            margin: 0 20px;
        }

        nav ul li a {
            color: white;
            text-decoration: none;
            font-size: 18px;
        }

        nav ul li a:hover {
            color: #ff6347;
        }

        /* Header Section */
        header {
            background-color: #f4f4f4;
            text-align: center;
            padding: 50px;
        }

        header h1 {
            font-size: 3rem;
        }

        /* About Section */
        .about {
            padding: 30px;
            background-color: #fff;
            text-align: center;
        }

        .about h2 {
            font-size: 2.5rem;
        }

        /* Contact Section */
        .contact {
            background-color: #333;
            color: white;
            padding: 30px;
            text-align: center;
        }

        .contact form {
            margin: 0 auto;
            width: 60%;
            max-width: 500px;
        }

        .contact input, .contact textarea {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
        }

        .contact button {
            background-color: #ff6347;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        .contact button:hover {
            background-color: #e55347;
        }

        /* Footer Section */
        footer {
            background-color: #333;
            color: white;
            text-align: center;
            padding: 20px;
        }

    </style>
</head>
<body>
    <!-- Navigation Bar -->
    <nav>
        <ul>
            <li><a href="#home">Home</a></li>
            <li><a href="#about">About</a></li>
            <li><a href="#contact">Contact</a></li>
        </ul>
    </nav>

    <!-- Header Section -->
    <header id="home">
        <h1>Welcome to My Simple Website</h1>
        <p>Your one-stop solution for everything!</p>
    </header>

    <!-- About Section -->
    <section class="about" id="about">
        <h2>About Us</h2>
        <p>We are a passionate team dedicated to creating amazing websites and providing exceptional services. We specialize in web design, development, and digital marketing.</p>
    </section>

    <!-- Contact Section -->
    <section class="contact" id="contact">
        <h2>Contact Us</h2>
        <form action="#" method="post">
            <input type="text" name="name" placeholder="Your Name" required>
            <input type="email" name="email" placeholder="Your Email" required>
            <textarea name="message" placeholder="Your Message" rows="5" required></textarea>
            <button type="submit">Send Message</button>
        </form>
    </section>

    <!-- Footer Section -->
    <footer>
        <p>&copy; 2024 My Simple Website. All rights reserved.</p>
    </footer>

</body>
</html>

