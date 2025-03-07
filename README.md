<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Colorful Portfolio</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f0f8ff;
            color: #333;
        }
        header {
            background: linear-gradient(90deg, #ff6f61, #6a5acd);
            color: white;
            padding: 20px 0;
            text-align: center;
        }
        nav {
            margin: 20px 0;
        }
        nav a {
            color: white;
            margin: 0 15px;
            text-decoration: none;
            font-weight: bold;
            transition: color 0.3s;
        }
        nav a:hover {
            color: #ffeb3b;
        }
        section {
            padding: 20px;
            margin: 20px;
            background: white;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
        }
        h2 {
            color: #ff6f61;
        }
        .projects {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
        }
        .project {
            background: #e0f7fa;
            border-radius: 8px;
            padding: 15px;
            margin: 10px;
            flex: 1 1 calc(30% - 20px);
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s;
        }
        .project:hover {
            transform: scale(1.05);
        }
        form {
            display: flex;
            flex-direction: column;
        }
        input, textarea {
            margin: 10px 0;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        button {
            background: #6a5acd;
            color: white;
            border: none;
            padding: 10px;
            border-radius: 4px;
            cursor: pointer;
            transition: background 0.3s;
        }
        button:hover {
            background: #483d8b;
        }
        footer {
            text-align: center;
            padding: 20px 0;
            background: linear-gradient(90deg, #ff6f61, #6a5acd);
            color: white;
            position: relative;
            bottom: 0;
            width: 100%;
        }
    </style>
</head>
<body>

<header>
    <h1>Welcome to My Colorful Portfolio</h1>
    <nav>
        <a href="#about">About</a>
        <a href="#projects">Projects</a>
        <a href="#contact">Contact</a>
    </nav>
</header>

<section id="about">
    <h2>About Me</h2>
    <p>Hello! I'm a passionate web developer with a knack for creating beautiful and functional websites. I love coding and am always eager to learn new technologies.</p>
</section>

<section id="projects">
    <h2>My Projects</h2>
    <div class="projects">
        <div class="project">
            <h3>Project One</h3>
            <p>A brief description of my first project. It showcases my skills in HTML, CSS, and JavaScript.</p>
        </div>
        <div class="project">
            <h3>Project Two</h3>
            <p>A brief description of my second project. It involves responsive design and modern web practices.</p>
        </div>
        <div class="project">
            <h3>Project Three</h3>
            <p>A brief description of my third project. It highlights my ability to work with APIs and backend technologies.</p>
        </div>
    </div>
</section>

<section id="contact">
    <h2>Contact Me</h2>
    <form onsubmit="return sendMessage();">
        <input type="text" id="name" placeholder="Your Name" required>
        <input type="email" id="email" placeholder="Your Email" required>
        <textarea id="message" rows="5
