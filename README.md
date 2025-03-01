 <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Advanced AI Chatbot</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: #121212;
            color: #fff;
            display: flex;
            flex-direction: column;
            height: 100vh;
        }
        
        .header {
            background: #222;
            padding: 15px 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 1px solid #333;
        }
        
        .title {
            font-size: 1.5rem;
            font-weight: bold;
            display: flex;
            align-items: center;
        }
        
        .title-icon {
            margin-right: 10px;
            color: #10a37f;
        }
        
        .time-display {
            font-size: 1rem;
            color: #10a37f;
            font-weight: bold;
        }
        
        .settings-btn {
            background: none;
            border: none;
            color: #fff;
            cursor: pointer;
            font-size: 1.2rem;
        }
        
        .chat-container {
            flex: 1;
            overflow-y: auto;
            padding: 20px;
        }
        
        .message {
            margin-bottom: 20px;
            display: flex;
            flex-direction: column;
        }
        
        .message-header {
            display: flex;
            align-items: center;
            margin-bottom: 5px;
        }
        
        .avatar {
            width: 30px;
            height: 30px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-right: 10px;
            font-weight: bold;
        }
        
        .user-avatar {
            background: #4a6ee0;
        }
        
        .bot-avatar {
            background: #10a37f;
        }
        
        .message-time {
            font-size: 0.8rem;
            color: #888;
            margin-left: 10px;
        }
        
        .message-content {
            padding: 12px 15px;
            border-radius: 15px;
            max-width: 80%;
            line-height: 1.4;
            font-size: 0.95rem;
        }
        
        .user-message .message-content {
            background: #4a6ee0;
            margin-left: 40px;
            border-top-left-radius: 5px;
        }
        
        .bot-message .message-content {
            background: #2d2d2d;
            margin-left: 40px;
            border-top-left-radius: 5px;
        }
        
        .user-message {
            align-self: flex-end;
        }
        
        .bot-message {
            align-self: flex-start;
        }
        
        .typing-indicator {
            display: flex;
            padding: 15px;
        }
        
        .typing-dot {
            width: 8px;
            height: 8px;
            background: #10a37f;
            border-radius: 50%;
            margin: 0 3px;
            opacity: 0.6;
            animation: typing-animation 1.5s infinite;
        }
        
        .typing-dot:nth-child(2) {
            animation-delay: 0.2s;
        }
        
        .typing-dot:nth-child(3) {
            animation-delay: 0.4s;
        }
        
        @keyframes typing-animation {
            0% { opacity: 0.6; transform: scale(1); }
            50% { opacity: 1; transform: scale(1.2); }
            100% { opacity: 0.6; transform: scale(1); }
        }
        
        .input-area {
            padding: 15px;
            background: #222;
            display: flex;
            align-items: center;
            border-top: 1px solid #333;
        }
        
        .input-field {
            flex: 1;
            padding: 12px 15px;
            border-radius: 20px;
            border: 1px solid #444;
            background: #2d2d2d;
            color: #fff;
            font-size: 0.95rem;
            resize: none;
            height: 50px;
            max-height: 120px;
            overflow-y: auto;
        }
        
        .input-field:focus {
            outline: none;
            border-color: #10a37f;
        }
        
        .send-btn {
            background: #10a37f;
            color: white;
            border: none;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-left: 10px;
            cursor: pointer;
            transition: background 0.3s;
        }
        
        .send-btn:hover {
            background: #0d8c6d;
        }
        
        .send-btn:disabled {
            background: #0d8c6d;
            opacity: 0.5;
            cursor: not-allowed;
        }
        
        .settings-panel {
            position: fixed;
            top: 0;
            right: -300px;
            width: 300px;
            height: 100vh;
            background: #222;
            padding: 20px;
            transition: right 0.3s;
            z-index: 1000;
            overflow-y: auto;
        }
        
        .settings-panel.open {
            right: 0;
        }
        
        .close-settings {
            position: absolute;
            top: 15px;
            right: 15px;
            background: none;
            border: none;
            color: #fff;
            font-size: 1.5rem;
            cursor: pointer;
        }
        
        .settings-title {
            font-size: 1.3rem;
            margin-bottom: 20px;
            border-bottom: 1px solid #333;
            padding-bottom: 10px;
        }
        
        .settings-section {
            margin-bottom: 20px;
        }
        
        .settings-section-title {
            font-size: 1rem;
            margin-bottom: 10px;
            color: #10a37f;
        }
        
        .settings-option {
            margin-bottom: 15px;
        }
        
        .settings-label {
            display: block;
            margin-bottom: 5px;
        }
        
        .settings-input, .settings-select {
            width: 100%;
            padding: 8px 10px;
            background: #2d2d2d;
            border: 1px solid #444;
            border-radius: 5px;
            color: #fff;
        }
        
        .settings-input:focus, .settings-select:focus {
            outline: none;
            border-color: #10a37f;
        }
        
        .settings-checkbox {
            margin-right: 8px;
        }
        
        .creator-info {
            position: fixed;
            bottom: 70px;
            right: 15px;
            background: rgba(16, 163, 127, 0.2);
            padding: 5px 10px;
            border-radius: 15px;
            font-size: 0.8rem;
            color: #10a37f;
        }
        
        .overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            display: none;
            z-index: 999;
        }
        
        .overlay.open {
            display: block;
        }
        
        /* For code blocks in bot responses */
        .code-block {
            background: #1a1a1a;
            padding: 10px;
            margin: 10px 0;
            border-radius: 5px;
            overflow-x: auto;
            font-family: monospace;
            border-left: 3px solid #10a37f;
        }
    </style>
</head>
<body>
    <div class="header">
        <div class="title">
            <div class="title-icon">🤖</div>
            Advanced AI Chatbot
        </div>
        <div class="time-display" id="current-time">00:00:00</div>
        <button class="settings-btn" id="open-settings">⚙️</button>
    </div>
    
    <div class="chat-container" id="chat-container">
        <!-- Messages will be added here -->
    </div>
    
    <div class="input-area">
        <textarea id="user-input" class="input-field" placeholder="Ask me anything..." rows="1"></textarea>
        <button id="send-btn" class="send-btn">
            <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M22 2L11 13" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                <path d="M22 2L15 22L11 13L2 9L22 2Z" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
        </button>
    </div>
    
    <div class="creator-info">
        Created by Surya
    </div>
    
    <div class="overlay" id="overlay"></div>
    
    <div class="settings-panel" id="settings-panel">
        <button class="close-settings" id="close-settings">×</button>
        <h2 class="settings-title">Chatbot Settings</h2>
        
        <div class="settings-section">
            <h3 class="settings-section-title">AI Model</h3>
            <div class="settings-option">
                <label class="settings-label" for="ai-model">Select AI Model</label>
                <select class="settings-select" id="ai-model">
                    <option value="gpt4">Advanced GPT-4</option>
                    <option value="claude">Claude 3</option>
                    <option value="llama">Llama 3</option>
                    <option value="custom">Custom Model</option>
                </select>
            </div>
            <div class="settings-option">
                <label class="settings-label" for="temperature">Temperature</label>
                <input type="range" class="settings-input" id="temperature" min="0" max="1" step="0.1" value="0.7">
                <span id="temperature-value">0.7</span>
            </div>
        </div>
        
        <div class="settings-section">
            <h3 class="settings-section-title">Response Settings</h3>
            <div class="settings-option">
                <label class="settings-label">
                    <input type="checkbox" class="settings-checkbox" id="code-highlighting" checked>
                    Enable code highlighting
                </label>
            </div>
            <div class="settings-option">
                <label class="settings-label">
                    <input type="checkbox" class="settings-checkbox" id="markdown-support" checked>
                    Enable markdown support
                </label>
            </div>
            <div class="settings-option">
                <label class="settings-label" for="max-length">Max response length</label>
                <select class="settings-select" id="max-length">
                    <option value="500">Short</option>
                    <option value="1500" selected>Medium</option>
                    <option value="5000">Long</option>
                    <option value="unlimited">Unlimited</option>
                </select>
            </div>
        </div>
        
        <div class="settings-section">
            <h3 class="settings-section-title">Personality</h3>
            <div class="settings-option">
                <label class="settings-label" for="personality">Bot Personality</label>
                <select class="settings-select" id="personality">
                    <option value="helpful">Helpful Assistant</option>
                    <option value="expert">Technical Expert</option>
                    <option value="creative">Creative Writer</option>
                    <option value="friend">Friendly Companion</option>
                    <option value="custom">Custom Personality</option>
                </select>
            </div>
            <div class="settings-option" id="custom-personality-container" style="display: none;">
                <label class="settings-label" for="custom-personality">Custom Personality Description</label>
                <textarea class="settings-input" id="custom-personality" rows="3" placeholder="Describe the personality you want..."></textarea>
            </div>
        </div>
        
        <div class="settings-section">
            <h3 class="settings-section-title">API Configuration</h3>
            <div class="settings-option">
                <label class="settings-label" for="api-key">API Key</label>
                <input type="password" class="settings-input" id="api-key" placeholder="Enter your API key">
            </div>
            <div class="settings-option">
                <label class="settings-label" for="api-endpoint">API Endpoint (Advanced)</label>
                <input type="text" class="settings-input" id="api-endpoint" placeholder="Custom API endpoint URL">
            </div>
        </div>
    </div>

    <script>
        // Initialize chat with a welcome message
        document.addEventListener('DOMContentLoaded', function() {
            // Update time display
            updateTime();
            setInterval(updateTime, 1000);
            
            // Add welcome message
            setTimeout(() => {
                addBotMessage("Hello! I'm your advanced AI assistant. How can I help you today?");
            }, 500);
            
            // Setup event listeners
            setupEventListeners();
            
            // Load saved settings if any
            loadSettings();
        });
        
        // Update time display
        function updateTime() {
            const now = new Date();
            const timeString = now.toLocaleTimeString();
            document.getElementById('current-time').textContent = timeString;
        }
        
        // Setup all event listeners
        function setupEventListeners() {
            // Send button click
            document.getElementById('send-btn').addEventListener('click', handleUserInput);
            
            // Enter key press in input field
            document.getElementById('user-input').addEventListener('keydown', function(e) {
                if (e.key === 'Enter' && !e.shiftKey) {
                    e.preventDefault();
                    handleUserInput();
                }
                
                // Auto-resize textarea
                setTimeout(() => {
                    this.style.height = 'auto';
                    const newHeight = Math.min(this.scrollHeight, 120);
                    this.style.height = newHeight + 'px';
                }, 0);
            });
            
            // Settings panel toggle
            document.getElementById('open-settings').addEventListener('click', function() {
                document.getElementById('settings-panel').classList.add('open');
                document.getElementById('overlay').classList.add('open');
            });
            
            document.getElementById('close-settings').addEventListener('click', closeSettings);
            document.getElementById('overlay').addEventListener('click', closeSettings);
            
            // Custom personality toggle
            document.getElementById('personality').addEventListener('change', function() {
                const container = document.getElementById('custom-personality-container');
                if (this.value === 'custom') {
                    container.style.display = 'block';
                } else {
                    container.style.display = 'none';
                }
            });
            
            // Temperature slider value display
            document.getElementById('temperature').addEventListener('input', function() {
                document.getElementById('temperature-value').textContent = this.value;
            });
        }
        
        // Close settings panel
        function closeSettings() {
            document.getElementById('settings-panel').classList.remove('open');
            document.getElementById('overlay').classList.remove('open');
            saveSettings();
        }
        
        // Save settings to localStorage
        function saveSettings() {
            const settings = {
                model: document.getElementById('ai-model').value,
                temperature: document.getElementById('temperature').value,
                codeHighlighting: document.getElementById('code-highlighting').checked,
                markdownSupport: document.getElementById('markdown-support').checked,
                maxLength: document.getElementById('max-length').value,
                personality: document.getElementById('personality').value,
                customPersonality: document.getElementById('custom-personality').value,
                apiKey: document.getElementById('api-key').value,
                apiEndpoint: document.getElementById('api-endpoint').value
            };
            
            localStorage.setItem('chatbotSettings', JSON.stringify(settings));
        }
        
        // Load settings from localStorage
        function loadSettings() {
            const savedSettings = localStorage.getItem('chatbotSettings');
            
            if (savedSettings) {
                const settings = JSON.parse(savedSettings);
                
                document.getElementById('ai-model').value = settings.model || 'gpt4';
                document.getElementById('temperature').value = settings.temperature || 0.7;
                document.getElementById('temperature-value').textContent = settings.temperature || 0.7;
                document.getElementById('code-highlighting').checked = settings.codeHighlighting !== false;
                document.getElementById('markdown-support').checked = settings.markdownSupport !== false;
                document.getElementById('max-length').value = settings.maxLength || '1500';
                document.getElementById('personality').value = settings.personality || 'helpful';
                document.getElementById('custom-personality').value = settings.customPersonality || '';
                document.getElementById('api-key').value = settings.apiKey || '';
                document.getElementById('api-endpoint').value = settings.apiEndpoint || '';
                
                // Show/hide custom personality field
                if (settings.personality === 'custom') {
                    document.getElementById('custom-personality-container').style.display = 'block';
                }
            }
        }
        
        // Handle user input
        function handleUserInput() {
            const inputField = document.getElementById('user-input');
            const userMessage = inputField.value.trim();
            
            if (!userMessage) return;
            
            // Add user message to chat
            addUserMessage(userMessage);
            
            // Clear input field
            inputField.value = '';
            inputField.style.height = '50px';
            
            // Show typing indicator
            showTypingIndicator();
            
            // Process the message and generate a response
            setTimeout(() => {
                generateResponse(userMessage);
            }, 1000);
        }
        
        // Add user message to chat
        function addUserMessage(message) {
            const chatContainer = document.getElementById('chat-container');
            const now = new Date();
            const timeString = now.toLocaleTimeString();
            
            const messageElement = document.createElement('div');
            messageElement.className = 'message user-message';
            
            messageElement.innerHTML = `
                <div class="message-header">
                    <div class="avatar user-avatar">U</div>
                    <span>You</span>
                    <span class="message-time">${timeString}</span>
                </div>
                <div class="message-content">${escapeHTML(message)}</div>
            `;
            
            chatContainer.appendChild(messageElement);
            scrollToBottom();
        }
        
        // Add bot message to chat
        function addBotMessage(message) {
            // Remove typing indicator if present
            const typingIndicator = document.querySelector('.typing-indicator');
            if (typingIndicator) {
                typingIndicator.remove();
            }
            
            const chatContainer = document.getElementById('chat-container');
            const now = new Date();
            const timeString = now.toLocaleTimeString();
            
            const messageElement = document.createElement('div');
            messageElement.className = 'message bot-message';
            
            // Process message content (code highlighting, etc.)
            const processedMessage = processMessageContent(message);
            
            messageElement.innerHTML = `
                <div class="message-header">
                    <div class="avatar bot-avatar">AI</div>
                    <span>AI Assistant</span>
                    <span class="message-time">${timeString}</span>
                </div>
                <div class="message-content">${processedMessage}</div>
            `;
            
            chatContainer.appendChild(messageElement);
            scrollToBottom();
        }
        
        // Show typing indicator
        function showTypingIndicator() {
            const chatContainer = document.getElementById('chat-container');
            
            const typingElement = document.createElement('div');
            typingElement.className = 'typing-indicator';
            
            typingElement.innerHTML = `
                <div class="avatar bot-avatar">AI</div>
                <div class="typing-dot"></div>
                <div class="typing-dot"></div>
                <div class="typing-dot"></div>
            `;
            
            chatContainer.appendChild(typingElement);
            scrollToBottom();
        }
        
        // Process message content to add code highlighting, etc.
        function processMessageContent(message) {
            // Check if code highlighting is enabled
            const codeHighlighting = document.getElementById('code-highlighting').checked;
            
            // Simple code block detection and highlighting (expand as needed)
            if (codeHighlighting) {
                // Replace code blocks (```code```) with styled divs
                message = message.replace(/```(\w*)\n([\s\S]*?)```/g, function(match, language, code) {
                    return `<div class="code-block" data-language="${language || 'text'}">${escapeHTML(code)}</div>`;
                });
                
                // Replace inline code (`code`) with styled spans
                message = message.replace(/`([^`]+)`/g, '<code>$1</code>');
            }
            
            // Add simple markdown support if enabled
            const markdownSupport = document.getElementById('markdown-support').checked;
            if (markdownSupport) {
                // Bold: **text** or __text__
                message = message.replace(/\*\*(.*?)\*\*|__(.*?)__/g, '<strong>$1$2</strong>');
                
                // Italic: *text* or _text_
                message = message.replace(/\*(.*?)\*|_(.*?)_/g, '<em>$1$2</em>');
                
                // Simple headers: # Header, ## Header, ### Header
                message = message.replace(/^# (.*$)/gm, '<h1>$1</h1>');
                message = message.replace(/^## (.*$)/gm, '<h2>$1</h2>');
                message = message.replace(/^### (.*$)/gm, '<h3>$1</h3>');
                
                // Links: [text](url)
                message = message.replace(/\[(.*?)\]\((.*?)\)/g, '<a href="$2" target="_blank">$1</a>');
                
                // Line breaks
                message = message.replace(/\n/g, '<br>');
            }
            
            return message;
        }
        
        // Scroll chat to bottom
        function scrollToBottom() {
            const chatContainer = document.getElementById('chat-container');
            chatContainer.scrollTop = chatContainer.scrollHeight;
        }
        
        // Escape HTML to prevent XSS
        function escapeHTML(text) {
            const div = document.createElement('div');
            div.textContent = text;
            return div.innerHTML;
        }
        
        // Generate AI response (simulated)
        function generateResponse(userMessage) {
            // Get current settings
            const model = document.getElementById('ai-model').value;
            const personality = document.getElementById('personality').value;
            const maxLength = document.getElementById('max-length').value;
            
            // In a real implementation, this would call an API
            // For demo purposes, we'll just simulate responses
            
            let response = "";
            const lowerMessage = userMessage.toLowerCase();
            
            // Simple pattern matching for demo purposes
            if (lowerMessage.includes('hello') || lowerMessage.includes('hi')) {
                response = "Hello! How can I assist you today?";
            } 
            else if (lowerMessage.includes('who are you') || lowerMessage.includes('what are you')) {
                response = "I'm an advanced AI assistant created to help answer questions and assist with various tasks. I was created by Surya. How can I help you?";
            }
            else if (lowerMessage.includes('weather')) {
                response = "I don't have access to real-time weather data, but I can help you find a reliable weather service or explain how weather forecasting works.";
            }
            else if (lowerMessage.includes('code') || lowerMessage.includes('programming')) {
                response = "I can help with programming questions. Here's an example of a simple JavaScript function:\n\n```javascript\nfunction greet(name) {\n  return `Hello, ${name}! Welcome to the AI chat.`;\n}\n\n// Example usage\nconsole.log(greet('User'));\n```\n\nWhat programming language are you interested in?";
            }
            else if (lowerMessage.includes('time')) {
                const now = new Date();
                response = `The current time is ${now.toLocaleTimeString()}. I also display the current time at the top of this chat interface for your convenience.`;
            }
            else if (lowerMessage.includes('help')) {
                response = "I can help with a wide range of topics including:\n- Answering questions\n- Programming assistance\n- Creative writing\n- Explanations of concepts\n- Problem-solving\n\nJust let me know what you need!";
            }
            else {
                // Default response
                response = "Thank you for your message. Based on my " + model + " capabilities and " + personality + " personality settings, I would typically provide a detailed response here. In a production environment, this would connect to an actual AI API. What else would you like to know?";
            }
            
            // Add bot message to chat
            addBotMessage(response);
        }
    </script>
</body>
</html>
