<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Multi-AI Chatbot</title>
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
        .typing-indicator {
            display: flex;
            padding: 10px;
        }
        .typing-dot {
            width: 8px;
            height: 8px;
            background: white;
            border-radius: 50%;
            margin: 0 3px;
            animation: typing 1.5s infinite;
        }
        .typing-dot:nth-child(2) { animation-delay: 0.2s; }
        .typing-dot:nth-child(3) { animation-delay: 0.4s; }
        @keyframes typing {
            0% { opacity: 0.3; transform: scale(1); }
            50% { opacity: 1; transform: scale(1.2); }
            100% { opacity: 0.3; transform: scale(1); }
        }
    </style>
</head>
<body>

    <h2>Multi-AI Chatbot</h2>
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
                <td>ChatGPT</td>
                <td><input type="password" id="openai-key" placeholder="Enter OpenAI Key"></td>
            </tr>
            <tr>
                <td>Claude</td>
                <td><input type="password" id="claude-key" placeholder="Enter Claude Key"></td>
            </tr>
            <tr>
                <td>Gemini</td>
                <td><input type="password" id="gemini-key" placeholder="Enter Gemini Key"></td>
            </tr>
        </table>
        <select id="ai-model">
            <option value="chatgpt">ChatGPT</option>
            <option value="claude">Claude</option>
            <option value="gemini">Gemini</option>
        </select>
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

            showTypingIndicator();
            fetchAIResponse(message);
        }

        function addMessage(sender, text, className) {
            const messageDiv = document.createElement('div');
            messageDiv.className = `message ${className}`;
            messageDiv.innerHTML = `<strong>${sender}:</strong> ${text}`;
            chatContainer.appendChild(messageDiv);
            chatContainer.scrollTop = chatContainer.scrollHeight;
        }

        function showTypingIndicator() {
            const typingDiv = document.createElement('div');
            typingDiv.className = 'typing-indicator';
            typingDiv.innerHTML = '<span class="typing-dot"></span><span class="typing-dot"></span><span class="typing-dot"></span>';
            chatContainer.appendChild(typingDiv);
            chatContainer.scrollTop = chatContainer.scrollHeight;
        }

        async function fetchAIResponse(userMessage) {
            const model = document.getElementById('ai-model').value;
            let apiKey, endpoint, requestBody;

            if (model === "chatgpt") {
                apiKey = document.getElementById('openai-key').value;
                endpoint = "https://api.openai.com/v1/chat/completions";
                requestBody = {
                    model: "gpt-4",
                    messages: [{ role: "user", content: userMessage }],
                    max_tokens: 200
                };
            } else if (model === "claude") {
                apiKey = document.getElementById('claude-key').value;
                endpoint = "https://api.anthropic.com/v1/messages";
                requestBody = {
                    model: "claude-3",
                    prompt: userMessage,
                    max_tokens: 200
                };
            } else if (model === "gemini") {
                apiKey = document.getElementById('gemini-key').value;
                endpoint = "https://generativelanguage.googleapis.com/v1/models/gemini:generateText?key=" + apiKey;
                requestBody = {
                    prompt: { text: userMessage }
                };
            }

            try {
                const response = await fetch(endpoint, {
                    method: "POST",
                    headers: {
                        "Authorization": `Bearer ${apiKey}`,
                        "Content-Type": "application/json"
                    },
                    body: JSON.stringify(requestBody)
                });

                const data = await response.json();
                document.querySelector('.typing-indicator').remove();
                addMessage("AI", JSON.stringify(data), "bot-message"); // Modify this to extract actual AI response
            } catch (error) {
                document.querySelector('.typing-indicator').remove();
                addMessage("AI", "Error fetching response. Check the console.", "bot-message");
                console.error(error);
            }
        }
    </script>

</body>
</html>

