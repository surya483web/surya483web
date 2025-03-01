 <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI Chatbot</title>
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

    <h2>AI Chatbot</h2>
    <div class="chat-container" id="chat-container"></div>

    <div class="input-container">
        <input type="text" id="user-input" class="input-field" placeholder="Ask me anything...">
        <button id="voice-btn" class="send-btn">🎤</button>
        <button id="send-btn" class="send-btn">Send</button>
    </div>

    <script>
        const chatContainer = document.getElementById('chat-container');
        const userInput = document.getElementById('user-input');
        const sendBtn = document.getElementById('send-btn');

        // API Key (Replace with your OpenAI API Key)
        const API_KEY = "YOUR_API_KEY";
        const API_ENDPOINT = "https://api.openai.com/v1/chat/completions";

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
            try {
                const response = await fetch(API_ENDPOINT, {
                    method: "POST",
                    headers: {
                        "Authorization": `Bearer ${API_KEY}`,
                        "Content-Type": "application/json"
                    },
                    body: JSON.stringify({
                        model: "gpt-4",
                        messages: [{ role: "user", content: userMessage }],
                        max_tokens: 200
                    })
                });

                const data = await response.json();
                document.querySelector('.typing-indicator').remove();
                const botResponse = data.choices[0].message.content;
                addMessage("AI", botResponse, "bot-message");
            } catch (error) {
                document.querySelector('.typing-indicator').remove();
                addMessage("AI", "Error fetching response. Check your API key.", "bot-message");
            }
        }

        // Voice Input (Speech-to-Text)
        document.getElementById('voice-btn').addEventListener('click', () => {
            const recognition = new (window.SpeechRecognition || window.webkitSpeechRecognition)();
            recognition.lang = 'en-US';

            recognition.onresult = (event) => {
                userInput.value = event.results[0][0].transcript;
                handleUserInput();
            };

            recognition.start();
        });
    </script>

</body>
</html>
