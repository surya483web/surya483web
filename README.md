 <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login Page</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 50px;
        }
        .container {
            width: 300px;
            margin: auto;
            padding: 20px;
            border: 1px solid #ccc;
            border-radius: 10px;
            box-shadow: 2px 2px 10px rgba(0,0,0,0.2);
        }
        input {
            width: 90%;
            padding: 8px;
            margin: 10px 0;
        }
        button {
            width: 100%;
            padding: 10px;
            background-color: blue;
            color: white;
            border: none;
            cursor: pointer;
        }
        .error {
            color: red;
        }
        .success {
            color: green;
        }
    </style>
</head>
<body>
    <div class="container">
        <h2>Login</h2>
        <input type="text" id="username" placeholder="Enter Username" required>
        <input type="password" id="password" placeholder="Enter Password" required>
        <button onclick="validateLogin()">Login</button>
        <p id="message"></p>
    </div>

    <script>
        function validateLogin() {
            var username = document.getElementById("username").value;
            var password = document.getElementById("password").value;
            var message = document.getElementById("message");

            var correctPassword = "Surya@123";
            var successMessages = [
                "Welcome, " + username + "! You have successfully logged in.",
                "Login successful! Have a great day, " + username + "!",
                "Access granted! Enjoy your time here, " + username + "!",
                "You are now logged in! Welcome aboard, " + username + "!"
            ];

            if (password === correctPassword) {
                var randomMessage = successMessages[Math.floor(Math.random() * successMessages.length)];
                message.innerHTML = randomMessage;
                message.className = "success";
            } else {
                message.innerHTML = "Invalid password. Try again.";
                message.className = "error";
            }
        }
    </script>
</body>
</html>
