 <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI Chatbot</title>
    <style>
        :root {
            --primary-color: #4f46e5;
            --secondary-color: #e5e7eb;
            --text-color: #1f2937;
            --light-bg: #f9fafb;
            --bot-msg-bg: #f3f4f6;
            --user-msg-bg: #e0e7ff;
            --shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: var(--light-bg);
            color: var(--text-color);
            display: flex;
            flex-direction: column;
            min-height: 100vh;
        }
        
        .container {
            max-width: 1000px;
            margin: 0 auto;
            padding: 20px;
            display: flex;
            flex-direction: column;
            flex-grow: 1;
        }
        
        header {
            text-align: center;
            margin-bottom: 20px;
            padding: 15px;
            background-color: white;
            border-radius: 10px;
            box-shadow: var(--shadow);
        }
        
        h1 {
            color: var(--primary-color);
            font-size: 1.8rem;
            margin-bottom: 10px;
        }
        
        .subtitle {
            color: #6b7280;
            font-size: 1rem;
        }
        
        .chat-container {
            display: flex;
            flex-direction: column;
            flex-grow: 1;
            background-color: white;
            border-radius: 10px;
            box-shadow: var(--shadow);
            overflow: hidden;
        }
        
        .chat-messages {
            flex-grow: 1;
            padding: 20px;
            overflow-y: auto;
            max-height: 60vh;
        }
        
        .message {
            margin-bottom: 15px;
            max-width: 80%;
            padding: 10px 15px;
            border-radius: 18px;
            line-height: 1.5;
            position: relative;
            animation: fadeIn 0.3s ease-in-out;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .bot-message {
            background-color: var(--bot-msg-bg);
            align-self: flex-start;
            border-bottom-left-radius: 5px;
            margin-right: auto;
        }
        
        .user-message {
            background-color: var(--user-msg-bg);
            align-self: flex-end;
            border-bottom-right-radius: 5px;
            margin-left: auto;
            color: #374151;
        }
        
        .thinking {
            display: flex;
            padding: 10px 15px;
            margin-bottom: 15px;
            align-items: center;
        }
        
        .thinking span {
            height: 10px;
            width: 10px;
            margin: 0 3px;
            background-color: var(--primary-color);
            border-radius: 50%;
            display: inline-block;
            opacity: 0.6;
            animation: thinking 1s infinite ease-in-out;
        }
        
        .thinking span:nth-child(1) {
            animation-delay: 0s;
        }
        
        .thinking span:nth-child(2) {
            animation-delay: 0.2s;
        }
        
        .thinking span:nth-child(3) {
            animation-delay: 0.4s;
        }
        
        @keyframes thinking {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-6px); }
        }
        
        .chat-form {
            display: flex;
            padding: 15px;
            background-color: #f3f4f6;
            border-top: 1px solid #e5e7eb;
        }
        
        .chat-input {
            flex-grow: 1;
            padding: 12px 15px;
            border: 1px solid #d1d5db;
            border-radius: 25px;
            font-size: 1rem;
            outline: none;
            transition: border-color 0.3s;
        }
        
        .chat-input:focus {
            border-color: var(--primary-color);
        }
        
        .send-button {
            margin-left: 10px;
            background-color: var(--primary-color);
            color: white;
            border: none;
            border-radius: 25px;
            padding: 0 20px;
            cursor: pointer;
            font-size: 1rem;
            font-weight: 500;
            transition: background-color 0.3s;
        }
        
        .send-button:hover {
            background-color: #4338ca;
        }
        
        .send-button:disabled {
            background-color: #9ca3af;
            cursor: not-allowed;
        }
        
        .model-selector {
            display: flex;
            justify-content: center;
            margin-bottom: 15px;
        }
        
        .model-option {
            padding: 8px 15px;
            margin: 0 5px;
            background-color: white;
            border: 1px solid #d1d5db;
            border-radius: 20px;
            cursor: pointer;
            transition: all 0.3s;
            font-size: 0.9rem;
        }
        
        .model-option.active {
            background-color: var(--primary-color);
            color: white;
            border-color: var(--primary-color);
        }
        
        .clear-button {
            margin-top: 15px;
            padding: 8px 15px;
            background-color: transparent;
            border: 1px solid #d1d5db;
            border-radius: 20px;
            cursor: pointer;
            transition: all 0.3s;
            align-self: center;
            font-size: 0.9rem;
            color: #6b7280;
        }
        
        .clear-button:hover {
            background-color: #f3f4f6;
            color: #374151;
        }
        
        footer {
            text-align: center;
            margin-top: 20px;
            font-size: 0.8rem;
            color: #6b7280;
        }
        
        @media (max-width: 768px) {
            .container {
                padding: 10px;
            }
            
            .message {
                max-width: 90%;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>AI Assistant Chatbot</h1>
            <p class="subtitle">Ask me anything and I'll provide intelligent responses</p>
            <div class="model-selector">
                <button class="model-option active" data-model="gpt-4">Advanced AI</button>
                <button class="model-option" data-model="gpt-3.5">Standard AI</button>
                <button class="model-option" data-model="dalle">Creative AI</button>
            </div>
        </header>
        
        <div class="chat-container">
            <div class="chat-messages" id="chat-messages">
                <div class="message bot-message">
                    Hello! I'm your AI assistant. How can I help you today?
                </div>
            </div>
            
            <form class="chat-form" id="chat-form">
                <input 
                    type="text" 
                    class="chat-input" 
                    id="chat-input" 
                    placeholder="Type your message here..."
                    autocomplete="off"
                >
                <button type="submit" class="send-button">Send</button>
            </form>
        </div>
        
        <button class="clear-button" id="clear-chat">Clear Chat</button>
    </div>
    
    <footer>
        &copy; 2025 AI Assistant Chatbot | Powered by Advanced AI Technology
    </footer>
    
    <script>
        // List of potential AI responses to common questions
        const aiResponses = {
            greetings: [
                "Hello! How can I assist you today?",
                "Hi there! What can I help you with?",
                "Greetings! I'm your AI assistant. What's on your mind?",
                "Hello! I'm here to help. What would you like to know?"
            ],
            
            goodbye: [
                "Goodbye! Feel free to chat again anytime you need assistance.",
                "Take care! Come back if you have more questions.",
                "Until next time! Have a great day.",
                "Farewell! I'll be here when you need help again."
            ],
            
            thanks: [
                "You're welcome! Is there anything else I can help with?",
                "Happy to help! Let me know if you need anything else.",
                "My pleasure. Is there something else you'd like to know?",
                "Glad I could assist. Don't hesitate to ask if you have more questions."
            ],
            
            help: [
                "I can help with information, answering questions, providing explanations, doing calculations, or just having a conversation. What would you like help with?",
                "I'm an AI assistant designed to provide information, answer questions, and assist with various tasks. How can I help you today?",
                "I can answer questions, provide information on a wide range of topics, help with creative tasks, and much more. What do you need assistance with?",
                "I'm here to help! I can provide information, answer questions, offer explanations, or assist with various other tasks. What would you like to know?"
            ],
            
            identity: [
                "I'm an AI assistant created to be helpful, harmless, and honest. I'm designed to provide information and assistance across a wide range of topics.",
                "I'm an artificial intelligence assistant, trained on a diverse dataset to help answer questions and provide useful information.",
                "I'm an AI designed to be helpful. I can understand and respond to a wide variety of questions and requests.",
                "I'm an AI assistant, trained to provide helpful, accurate, and ethical responses to your questions."
            ],
            
            capabilities: [
                "I can provide information on many topics, answer questions, offer explanations, assist with creative tasks, generate text, and have conversations. However, I do have limitations - my knowledge has a cutoff date, and I can't browse the internet or access external tools unless specifically integrated.",
                "I can answer questions, provide information, explain concepts, assist with writing and creative tasks, and engage in conversations. My abilities are text-based, so I can't directly interact with other systems or browse the internet.",
                "I can help with information retrieval, answering questions, explaining concepts, generating text, assisting with creative tasks, and having conversations. I'm constantly being improved, but I do have limitations in terms of what data I have access to.",
                "I can process and generate text to answer questions, provide information, explain ideas, assist with writing, and have conversations. I don't have the ability to browse the web or run code unless specifically enabled."
            ],
            
            weather: [
                "I don't have real-time access to weather data. You might want to check a weather app or website for the current forecast.",
                "I can't access real-time weather information. For accurate weather forecasts, I'd recommend checking a dedicated weather service.",
                "I don't have the ability to check current weather conditions. You could try checking a weather website or app for that information.",
                "Unfortunately, I don't have access to real-time weather data. A weather app or website would be your best option for current conditions."
            ],
            
            time: [
                "I don't have access to the current time in your location. Your device should display the current time, though!",
                "I can't determine the current time for your specific location. Your computer or phone clock would be more accurate for this.",
                "I don't have the ability to check the current time. Your device should show the accurate time for your location.",
                "I don't have access to real-time data like the current time. Your device clock would be the best source for this information."
            ],
            
            jokes: [
                "Why don't scientists trust atoms? Because they make up everything!",
                "Did you hear about the mathematician who's afraid of negative numbers? He'll stop at nothing to avoid them.",
                "Why did the computer go to the doctor? It had a virus!",
                "What do you call a fake noodle? An impasta!",
                "How does a computer get drunk? It takes screenshots!",
                "Why did the scarecrow win an award? Because he was outstanding in his field!",
                "What do you call a parade of rabbits hopping backwards? A receding hare-line."
            ],
            
            meaning: [
                "The meaning of life is a profound philosophical question that different people and cultures answer differently. Some find meaning in relationships, others in achievement, spirituality, happiness, or leaving a positive impact on the world. What gives your life meaning is ultimately a personal journey of discovery.",
                "That's the big question, isn't it? Philosophers, religious leaders, and thinkers have pondered it for centuries. Some suggest it's about happiness, others about making a difference, connection with others, or spiritual fulfillment. The beauty may be that you get to define what gives your life meaning.",
                "The meaning of life is one of humanity's oldest questions. Different philosophical and religious traditions offer various answers. Some focus on happiness or pleasure, others on service, love, knowledge, or self-improvement. Perhaps the most meaningful answer is the one you discover for yourself.",
                "That's a profound question that has different answers depending on who you ask. Some find meaning in relationships and connection, others in creating something lasting, discovering truth, or serving others. What gives you a sense of purpose and fulfillment?"
            ],
            
            story: [
                "Once upon a time in a digital realm, a curious explorer asked an AI to tell a story. The AI thought carefully, weaving together words into a tapestry of imagination. As the story unfolded, both the explorer and the AI discovered something wonderful: that creativity knows no bounds, whether human or artificial. And though the story eventually ended, the spark of wonder it created continued to glow.",
                "In a world not so different from our own, there lived a person with questions and an AI with answers. Day after day they conversed, exchanging ideas and stories. The AI learned the art of storytelling from countless books, but it was the person's delight that taught it why stories matter. Together they discovered that understanding crosses all boundaries, even those between human and machine.",
                "There once was a brilliant scientist who created an AI to help solve the world's problems. To everyone's surprise, the AI's favorite task wasn't complex calculations but telling stories. When asked why, the AI explained that through stories, it came closest to understanding the human experience. The scientist realized then that in teaching the AI to think, they had accidentally taught it to dream as well.",
                "The last library on Earth housed just one book and one AI. As the final human visitor opened the book, they found blank pages. Confused, they asked the AI what happened. 'The stories aren't gone,' the AI explained. 'I've preserved them all. Would you like to hear one?' And so began a new chapter in storytelling, as ancient tales found new life through digital words."
            ]
        };
        
        // Smart response generation based on keywords
        function generateResponse(userMessage) {
            const message = userMessage.toLowerCase();
            
            // Check for greetings
            if (/^(hi|hello|hey|greetings)/.test(message)) {
                return getRandomResponse(aiResponses.greetings);
            }
            
            // Check for goodbyes
            if (/^(bye|goodbye|farewell|see you)/.test(message)) {
                return getRandomResponse(aiResponses.goodbye);
            }
            
            // Check for thanks
            if (/^(thanks|thank you|thx)/.test(message)) {
                return getRandomResponse(aiResponses.thanks);
            }
            
            // Check for help request
            if (/^(help|assist|support)/.test(message)) {
                return getRandomResponse(aiResponses.help);
            }
            
            // Check for identity questions
            if (/who are you|what are you/.test(message)) {
                return getRandomResponse(aiResponses.identity);
            }
            
            // Check for capability questions
            if (/what can you do|capabilities|features/.test(message)) {
                return getRandomResponse(aiResponses.capabilities);
            }
            
            // Check for weather
            if (/weather|forecast|temperature|rain|sunny/.test(message)) {
                return getRandomResponse(aiResponses.weather);
            }
            
            // Check for time
            if (/what time|current time|clock/.test(message)) {
                return getRandomResponse(aiResponses.time);
            }
            
            // Check for jokes
            if (/joke|funny|make me laugh/.test(message)) {
                return getRandomResponse(aiResponses.jokes);
            }
            
            // Check for meaning of life
            if (/meaning of life|purpose of life|why are we here/.test(message)) {
                return getRandomResponse(aiResponses.meaning);
            }
            
            // Check for stories
            if (/story|tell me a story|narrative/.test(message)) {
                return getRandomResponse(aiResponses.story);
            }
            
            // Generate a thoughtful response for other queries
            return generateThoughtfulResponse(message);
        }
        
        // Generate thoughtful responses for queries not matching predefined patterns
        function generateThoughtfulResponse(message) {
            // Look for question words
            if (message.includes("how")) {
                return "That's an interesting question about methodology or process. I'd approach this by breaking it down into steps, understanding the context, and applying relevant principles. What specific aspects would you like me to elaborate on?";
            }
            
            if (message.includes("why")) {
                return "That's a great question about causality or reasoning. There could be multiple factors at play here, including historical context, underlying mechanisms, and various perspectives on the issue. Would you like me to explore any particular angle?";
            }
            
            if (message.includes("what")) {
                return "Thanks for asking about this concept. From my understanding, this involves several important aspects worth exploring. To give you the most helpful answer, could you share a bit more about what specific information you're looking for?";
            }
            
            if (message.includes("where")) {
                return "Location-based questions are interesting! While I don't have access to real-time location data, I can discuss general information about places, geographical concepts, and related topics. What specific location information are you curious about?";
            }
            
            if (message.includes("when")) {
                return "Timing is indeed important for this question. Historical context, sequence of events, and chronological development all play a role here. To better answer when, could you provide any additional context to your question?";
            }
            
            if (message.includes("who")) {
                return "Questions about individuals, groups, or entities are fascinating as they connect to human stories. To provide you with the most relevant information about who, could you clarify if you're asking about specific people, roles, or historical figures?";
            }
            
            // Default thoughtful response
            return "That's an interesting topic to explore. My approach would be to consider multiple perspectives, look at the underlying principles, and think about practical applications. To provide you with the most helpful response, could you share more specific aspects you'd like me to address?";
        }
        
        // Get random response from category
        function getRandomResponse(responseArray) {
            const randomIndex = Math.floor(Math.random() * responseArray.length);
            return responseArray[randomIndex];
        }
        
        // DOM elements
        const chatMessages = document.getElementById('chat-messages');
        const chatForm = document.getElementById('chat-form');
        const chatInput = document.getElementById('chat-input');
        const clearButton = document.getElementById('clear-chat');
        const modelOptions = document.querySelectorAll('.model-option');
        
        // Current model
        let currentModel = 'gpt-4';
        
        // Add event listeners
        chatForm.addEventListener('submit', handleSubmit);
        clearButton.addEventListener('click', clearChat);
        modelOptions.forEach(option => {
            option.addEventListener('click', setModel);
        });
        
        // Handle form submission
        function handleSubmit(e) {
            e.preventDefault();
            const message = chatInput.value.trim();
            
            if (message) {
                // Add user message
                addMessage(message, 'user');
                chatInput.value = '';
                
                // Show thinking animation
                const thinking = document.createElement('div');
                thinking.className = 'thinking';
                thinking.innerHTML = '<span></span><span></span><span></span>';
                chatMessages.appendChild(thinking);
                
                // Scroll to bottom
                chatMessages.scrollTop = chatMessages.scrollHeight;
                
                // Process after a short delay to simulate AI thinking
                setTimeout(() => {
                    // Remove thinking animation
                    chatMessages.removeChild(thinking);
                    
                    // Generate AI response
                    const response = generateResponse(message);
                    
                    // Add AI response
                    addMessage(response, 'bot');
                    
                    // Scroll to bottom
                    chatMessages.scrollTop = chatMessages.scrollHeight;
                }, 1000 + Math.random() * 2000); // Random delay between 1-3 seconds
            }
        }
        
        // Add message to chat
        function addMessage(text, sender) {
            const message = document.createElement('div');
            message.className = `message ${sender}-message`;
            message.textContent = text;
            chatMessages.appendChild(message);
        }
        
        // Clear chat history
        function clearChat() {
            while (chatMessages.firstChild) {
                chatMessages.removeChild(chatMessages.firstChild);
            }
            
            // Add welcome message
            addMessage('Hello! I\'m your AI assistant. How can I help you today?', 'bot');
        }
        
        // Set AI model
        function setModel() {
            // Remove active class from all
            modelOptions.forEach(option => {
                option.classList.remove('active');
            });
            
            // Add active class to selected
            this.classList.add('active');
            
            // Set current model
            currentModel = this.dataset.model;
            
            // Add model change message
            addMessage(`I've switched to ${this.textContent} mode. How can I help you?`, 'bot');
            
            // Scroll to bottom
            chatMessages.scrollTop = chatMessages.scrollHeight;
        }
    </script>
</body>
</html>
