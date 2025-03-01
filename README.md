 <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gemini AI Chatbot</title>
    <style>
        body {
            background: #121212;
            color: white;
            font-family: Arial, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            height: 100vh;
            justify-content: center;
        }
        .chat-container {
            width: 400px;
            height: 500px;
            overflow-y: auto;
            border: 1px solid #444;
            border-radius: 10px;
            padding: 10px;
            background: #222;
        }
        .message {
            margin: 10px;
            padding: 10px;
            border-radius: 10px;
            max-width: 80%;
            line-height: 1.4;
        }
        .user-message {
            background: #4a6ee0;
            align-self: flex-end;
            text-align: right;
        }
        .bot-message {
            background: #333;
            align-self: flex-start;
        }
        .input-container {
            display: flex;
            width: 400px;
            margin-top: 10px;
        }
        .input-field {
            flex: 1;
            padding: 10px;
            border-radius: 5px;
            border: none;
            background: #444;
            color: white;
        }
        .send-btn {
            background: #10a37f;
            color: white;
            border: none;
            padding: 10px;
            cursor: pointer;
            border-radius: 5px;
            margin-left: 5px;
        }
        .settings-container {
            margin-top: 20px;
            width: 400px;
            background: #222;
            padding: 10px;
            border-radius: 10px;
            text-align: center;
        }
        .settings-table {
            width: 100%;
            border-collapse: collapse;
        }
        .settings-table th, .settings-table td {
            border: 1px solid #444;
            padding: 5px;
            text-align: center;
        }
    </style>
</head>
<body>

    <h2>Gemini AI Chatbot</h2>
    <div class="chat-container" id="chat-container"></div>

    <div class="input-container">
        <input type="text" id="user-input" class="input-field" placeholder="Ask me anything...">
        <button id="send-btn" class="send-btn">Send</button>
    </div>

    <div class="settings-container">
        <h3>API Settings</h3>
        <table class="settings-table">
            <tr>
                <th>AI Model</th>
                <th>API Key</th>
            </tr>
            <tr>
                <td>Gemini AI</td>
                <td><input type="password" id="gemini-key" placeholder="Enter Gemini API Key"></td>
            </tr>
        </table>
    </div>

    <script>
        const chatContainer = document.getElementById('chat-container');
        const userInput = document.getElementById('user-input');
        const sendBtn = document.getElementById('send-btn');

        sendBtn.addEventListener('click', handleUserInput);
        userInput.addEventListener('keydown', (event) => {
            if (event.key === 'Enter' && !event.shiftKey) {
                event.preventDefault();
                handleUserInput();
            }
        });

        function handleUserInput() {
            const message = userInput.value.trim();
            if (message === "") return;

            addMessage("You", message, "user-message");
            userInput.value = "";

            fetchAIResponse(message);
        }

        function addMessage(sender, text, className) {
            const messageDiv = document.createElement('div');
            messageDiv.className = `message ${className}`;
            messageDiv.innerHTML = `<strong>${sender}:</strong> ${text}`;
            chatContainer.appendChild(messageDiv);
            chatContainer.scrollTop = chatContainer.scrollHeight;
        }

        async function fetchAIResponse(userMessage) {
            const apiKey = document.getElementById('gemini-key').value;
            if (!apiKey) {
                addMessage("AI", "Please enter a valid Gemini API Key.", "bot-message");
                return;
            }

            const endpoint = `https://generativelanguage.googleapis.com/v1/models/gemini:generateText?key=${apiKey}`;
            const requestBody = {
                prompt: { text: userMessage }
            };

            try {
                const response = await fetch(endpoint, {
                    method: "POST",
                    headers: { "Content-Type": "application/json" },
                    body: JSON.stringify(requestBody)
                });

                const data = await response.json();
                if (data.candidates && data.candidates.length > 0) {
                    addMessage("AI", data.candidates[0].output, "bot-message");
                } else {
                    addMessage("AI", "No valid response received from Gemini AI.", "bot-message");
                }
            } catch (error) {
                addMessage("AI", "Error fetching response. Check the console.", "bot-message");
                console.error(error);
            }
        }
    </script>

</body>
</html>


