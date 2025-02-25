# app.py
from flask import Flask, render_template

app = Flask(__name__)

@app.route('/')
def index():
    return render_template('index.html')

if __name__ == '__main__':
    app.run(debug=True)

# Create a templates folder and add the following HTML file

# templates/index.html
"""
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f0f0f0;
            margin: 0;
        }
        
        .calculator {
            background-color: #333;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
            padding: 20px;
            width: 300px;
        }
        
        .display {
            background-color: #222;
            border-radius: 5px;
            color: white;
            font-size: 36px;
            height: 70px;
            margin-bottom: 20px;
            padding: 10px;
            text-align: right;
            overflow: hidden;
        }
        
        .buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            grid-gap: 10px;
        }
        
        button {
            background-color: #4d4d4d;
            border: none;
            border-radius: 5px;
            color: white;
            cursor: pointer;
            font-size: 24px;
            height: 60px;
            transition: background-color 0.2s;
        }
        
        button:hover {
            background-color: #666;
        }
        
        .clear, .equals {
            grid-column: span 2;
        }
        
        .operator {
            background-color: #ff9500;
        }
        
        .operator:hover {
            background-color: #ffb144;
        }
        
        .clear {
            background-color: #ff3b30;
        }
        
        .clear:hover {
            background-color: #ff6459;
        }
        
        .equals {
            background-color: #34c759;
        }
        
        .equals:hover {
            background-color: #4cd964;
        }
    </style>
</head>
<body>
    <div class="calculator">
        <div class="display" id="display">0</div>
        <div class="buttons">
            <button class="clear" onclick="clearDisplay()">Clear</button>
            <button class="operator" onclick="appendToDisplay('/')">/</button>
            <button class="operator" onclick="appendToDisplay('*')">×</button>
            <button onclick="appendToDisplay('7')">7</button>
            <button onclick="appendToDisplay('8')">8</button>
            <button onclick="appendToDisplay('9')">9</button>
            <button class="operator" onclick="appendToDisplay('-')">-</button>
            <button onclick="appendToDisplay('4')">4</button>
            <button onclick="appendToDisplay('5')">5</button>
            <button onclick="appendToDisplay('6')">6</button>
            <button class="operator" onclick="appendToDisplay('+')">+</button>
            <button onclick="appendToDisplay('1')">1</button>
            <button onclick="appendToDisplay('2')">2</button>
            <button onclick="appendToDisplay('3')">3</button>
            <button onclick="appendToDisplay('0')">0</button>
            <button onclick="appendToDisplay('.')">.</button>
            <button class="equals" onclick="calculate()">=</button>
        </div>
    </div>

    <script>
        let currentDisplay = '0';
        
        function updateDisplay() {
            document.getElementById('display').textContent = currentDisplay;
        }
        
        function appendToDisplay(value) {
            if (currentDisplay === '0' && value !== '.') {
                currentDisplay = value;
            } else {
                currentDisplay += value;
            }
            updateDisplay();
        }
        
        function clearDisplay() {
            currentDisplay = '0';
            updateDisplay();
        }
        
        function calculate() {
            try {
                currentDisplay = eval(currentDisplay).toString();
            } catch (error) {
                currentDisplay = 'Error';
            }
            updateDisplay();
        }
    </script>
</body>
</html>
"""

# Create a static folder for potential CSS and JS files if you want to separate them later
