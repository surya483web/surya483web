 <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Audio to Text Converter</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            max-width: 800px;
            margin: 0 auto;
            padding: 20px;
            line-height: 1.6;
        }
        h1 {
            color: #333;
            text-align: center;
        }
        .container {
            margin-top: 30px;
        }
        .controls {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin-bottom: 20px;
        }
        button {
            padding: 10px 20px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 16px;
            transition: background-color 0.3s;
        }
        #startRecording {
            background-color: #4CAF50;
            color: white;
        }
        #stopRecording {
            background-color: #f44336;
            color: white;
            display: none;
        }
        #transcript {
            border: 1px solid #ddd;
            padding: 15px;
            border-radius: 4px;
            min-height: 150px;
            max-height: 300px;
            overflow-y: auto;
            background-color: #f9f9f9;
        }
        .status {
            text-align: center;
            margin-bottom: 10px;
            font-style: italic;
            color: #666;
        }
        .final {
            color: #333;
        }
        .interim {
            color: #999;
        }
    </style>
</head>
<body>
    <h1>Audio to Text Converter</h1>
    
    <div class="container">
        <div class="status" id="status">Ready to record</div>
        
        <div class="controls">
            <button id="startRecording">Start Recording</button>
            <button id="stopRecording">Stop Recording</button>
        </div>
        
        <div id="transcript"></div>
    </div>
    
    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const startButton = document.getElementById('startRecording');
            const stopButton = document.getElementById('stopRecording');
            const transcript = document.getElementById('transcript');
            const status = document.getElementById('status');
            
            let recognition;
            let isRecording = false;
            let finalTranscript = '';
            
            // Check if browser supports speech recognition
            if (!('webkitSpeechRecognition' in window) && !('SpeechRecognition' in window)) {
                status.textContent = 'Speech recognition is not supported in this browser. Please try Chrome, Edge, or Safari.';
                startButton.disabled = true;
                return;
            }
            
            // Initialize speech recognition
            recognition = new (window.SpeechRecognition || window.webkitSpeechRecognition)();
            recognition.continuous = true;
            recognition.interimResults = true;
            recognition.lang = 'en-US'; // Default language
            
            // Handle results
            recognition.onresult = (event) => {
                let interimTranscript = '';
                
                for (let i = event.resultIndex; i < event.results.length; i++) {
                    const result = event.results[i];
                    const text = result[0].transcript;
                    
                    if (result.isFinal) {
                        finalTranscript += text + ' ';
                    } else {
                        interimTranscript += text;
                    }
                }
                
                transcript.innerHTML = `
                    <div class="final">${finalTranscript}</div>
                    <div class="interim">${interimTranscript}</div>
                `;
            };
            
            // Handle start
            recognition.onstart = () => {
                isRecording = true;
                status.textContent = 'Recording... Speak now';
                startButton.style.display = 'none';
                stopButton.style.display = 'inline-block';
            };
            
            // Handle end
            recognition.onend = () => {
                if (isRecording) {
                    // If still recording when onend fires, restart
                    recognition.start();
                } else {
                    status.textContent = 'Recording stopped';
                    startButton.style.display = 'inline-block';
                    stopButton.style.display = 'none';
                }
            };
            
            // Handle errors
            recognition.onerror = (event) => {
                status.textContent = `Error occurred: ${event.error}`;
                isRecording = false;
                startButton.style.display = 'inline-block';
                stopButton.style.display = 'none';
            };
            
            // Start recording
            startButton.addEventListener('click', () => {
                finalTranscript = '';
                transcript.innerHTML = '';
                isRecording = true;
                recognition.start();
            });
            
            // Stop recording
            stopButton.addEventListener('click', () => {
                isRecording = false;
                recognition.stop();
            });
        });
    </script>
</body>
</html>



