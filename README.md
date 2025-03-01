 <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gemini AI Chatbot</title>
    <style>
        body { font-family: Arial, sans-serif; margin: 20px; background-color: #f4f4f4; }
        #chatbox { width: 100%; height: 400px; border: 2px solid #4CAF50; border-radius: 10px; overflow-y: scroll; padding: 10px; background: white; }
        #userInput { width: 75%; padding: 10px; border-radius: 5px; border: 1px solid #ccc; }
        #sendButton { padding: 10px; background-color: #4CAF50; color: white; border: none; border-radius: 5px; cursor: pointer; }
        #sendButton:hover { background-color: #45a049; }
        .message { margin: 5px 0; padding: 5px; border-radius: 5px; }
        .user { background-color: #d1e7dd; text-align: right; }
        .bot { background-color: #f8d7da; text-align: left; }
        .timestamp { font-size: 12px; color: gray; }
    </style>
</head>
<body>
    <h2 style="color: #4CAF50; text-align: center;">Gemini AI Chatbot 🤖</h2>
    <div id="chatbox"></div>
    <input type="text" id="userInput" placeholder="Type a message...">
    <button id="sendButton">Send</button>

    <script>
        const apiKey = "YOUR_GEMINI_API_KEY"; // Replace with your Gemini API key
        const chatbox = document.getElementById("chatbox");
        const userInput = document.getElementById("userInput");
        const sendButton = document.getElementById("sendButton");

        function getTimeStamp() {
            const now = new Date();
            return now.toLocaleTimeString();
        }

        function appendMessage(role, message) {
            const messageDiv = document.createElement("div");
            messageDiv.classList.add("message", role);
            messageDiv.innerHTML = `<p><strong>${role === "user" ? "You" : "Bot"}:</strong> ${message}</p>`;
            messageDiv.innerHTML += `<span class='timestamp'>${getTimeStamp()}</span>`;
            chatbox.appendChild(messageDiv);
            chatbox.scrollTop = chatbox.scrollHeight;
        }

        function evaluateMath(input) {
            try {
                return eval(input);
            } catch {
                return "Invalid math expression.";
            }
        }

        async function sendMessage() {
            let message = userInput.value.trim();
            if (!message) return;

            appendMessage("user", message);
            userInput.value = "";

            if (/^\d+[\+\-\*\/]\d+$/.test(message)) {
                appendMessage("bot", "Math result: " + evaluateMath(message));
                return;
            }

            const response = await fetch("https://api.gemini.com/v1/chat/completions", {
                method: "POST",
                headers: {
                    "Content-Type": "application/json",
                    "Authorization": `Bearer ${apiKey}`
                },
                body: JSON.stringify({
                    model: "gemini-pro",
                    messages: [{ role: "user", content: message }]
                })
            });

            const data = await response.json();
            const botReply = data.choices[0]?.message?.content || "Error retrieving response";
            appendMessage("bot", botReply);
        }

        sendButton.addEventListener("click", sendMessage);
        userInput.addEventListener("keypress", function (e) {
            if (e.key === "Enter") sendMessage();
        });
    </script>
</body>
</html>

