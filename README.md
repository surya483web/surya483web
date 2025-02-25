
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI Chatbot</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background: linear-gradient(to right, #00c6ff, #0072ff);
        }
        .chat-container {
            width: 400px;
            background: white;
            border-radius: 10px;
            box-shadow: 0px 4px 10px rgba(0,0,0,0.2);
            overflow: hidden;
            display: flex;
            flex-direction: column;
        }
        .chat-box {
            height: 300px;
            overflow-y: auto;
            padding: 15px;
        }
        .message {
            padding: 10px;
            border-radius: 10px;
            margin: 5px 0;
            max-width: 80%;
        }
        .user-message {
            background-color: #007bff;
            color: white;
            align-self: flex-end;
        }
        .bot-message {
            background-color: #f1f1f1;
            align-self: flex-start;
        }
        .chat-input {
            display: flex;
            border-top: 1px solid #ccc;
            padding: 10px;
            background: white;
        }
        input {
            flex: 1;
            padding: 10px;
            border: none;
            border-radius: 5px;
            outline: none;
        }
        button {
            background: #007bff;
            color: white;
            border: none;
            padding: 10px;
            cursor: pointer;
            border-radius: 5px;
            margin-left: 10px;
        }
        button:hover {
            background: #0056b3;
        }
    </style>
</head>
<body>

    <div class="chat-container">
        <div class="chat-box" id="chat-box">
            <div class="message bot-message">Hello! How can I help you?</div>
        </div>
        <div class="chat-input">
            <input type="text" id="user-input" placeholder="Type a message..." onkeypress="handleKeyPress(event)">
            <button onclick="sendMessage()">Send</button>
        </div>
    </div>

    <script>
        function sendMessage() {
            let inputBox = document.getElementById("user-input");
            let message = inputBox.value.trim();
            if (message === "") return;

            let chatBox = document.getElementById("chat-box");

            // Append user message
            let userMessage = document.createElement("div");
            userMessage.className = "message user-message";
            userMessage.innerText = message;
            chatBox.appendChild(userMessage);

            // Scroll to latest message
            chatBox.scrollTop = chatBox.scrollHeight;

            // AI responses (simple pre-defined)
            let responses = [
                "I'm an AI chatbot! How can I assist you?",
                "That sounds interesting! Tell me more.",
                "I'm here to help!",
                "Can you elaborate on that?",
                "I'm still learning, but I can try to help!"
            ];

            let botResponse = responses[Math.floor(Math.random() * responses.length)];

            setTimeout(() => {
                let botMessage = document.createElement("div");
                botMessage.className = "message bot-message";
                botMessage.innerText = botResponse;
                chatBox.appendChild(botMessage);
                chatBox.scrollTop = chatBox.scrollHeight;
            }, 1000);

            inputBox.value = "";
        }

        function handleKeyPress(event) {
            if (event.key === "Enter") {
                sendMessage();
            }
        }
    </script>

</body>
</html>
