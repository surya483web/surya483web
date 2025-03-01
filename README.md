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
        .ai-selector {
            margin-bottom: 10px;
        }
    </style>
</head>
<body>

    <h2>AI Chatbot (ChatGPT, Claude, Gemini)</h2>

    <select id="ai-model" class="ai-selector">
        <option value="gpt-4">ChatGPT (GPT-4)</option>
        <option value="claude">Claude AI</option>
        <option value="gemini">Gemini AI</option>
    </select>

    <div class="chat-container" id="chat-container"></div>

    <div class="input-container">
        <input type="text" id="user-input" class="input-field" placeholder="Ask me anything...">
        <button id="send-btn" class="send-btn">Send</button>
    </div>

    <script>
        const chatContainer = document.getElementById('chat-container');
        const userInput = document.getElementById('user-input');
        const sendBtn = document.getElementById('send-btn');
        const aiModelSelector = document.getElementById('ai-model');

        // API Keys (Replace with your actual keys)
        const API_KEYS = {
            "gpt-4": "YOUR_OPENAI_API_KEY",
            "claude": "YOUR_CLAUDE_API_KEY",
            "gemini": "YOUR_GEMINI_API_KEY"
        };

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
            const selectedModel = aiModelSelector.value;
            const apiKey = API_KEYS[selectedModel];

            if (!apiKey) {
                addMessage("AI", "API key missing! Please update the script.", "bot-message");
                return;
            }

            let apiUrl = "";
            let requestBody = {};

            if (selectedModel === "gpt-4") {
                apiUrl = "https://api.openai.com/v1/chat/completions";
                requestBody = {
                    model: "gpt-4",
                    messages: [{ role: "user", content: userMessage }],
                    max_tokens: 200
                };
            } else if (selectedModel === "claude") {
                apiUrl = "https://api.anthropic.com/v1/complete";
                requestBody = {
                    prompt: userMessage,
                    model: "claude-3",
                    max_tokens_to_sample: 200
                };
            } else if (selectedModel === "gemini") {
                apiUrl = "https://generativelanguage.googleapis.com/v1beta/models/gemini-pro:generateText";
                requestBody = {
                    prompt: { text: userMessage },
                    temperature: 0.7
                };
            }

            try {
                const response = await fetch(apiUrl, {
                    method: "POST",
                    headers: {
                        "Authorization": `Bearer ${apiKey}`,
                        "Content-Type": "application/json"
                    },
                    body: JSON.stringify(requestBody)
                });

                const data = await response.json();
                console.log("API Response:", data);

                let botResponse = "I couldn't generate a response.";
                if (selectedModel === "gpt-4" && data.choices) {
                    botResponse = data.choices[0].message.content;
                } else if (selectedModel === "claude" && data.completion) {
                    botResponse = data.completion;
                } else if (selectedModel === "gemini" && data.candidates) {
                    botResponse = data.candidates[0].output;
                }

                addMessage("AI", botResponse, "bot-message");
            } catch (error) {
                console.error("API Fetch Error:", error);
                addMessage("AI", "Error fetching response. Check the console.", "bot-message");
            }
        }
    </script>

</body>
</html>
