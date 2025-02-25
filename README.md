from flask import Flask, render_template, request, redirect, url_for
import random

app = Flask(__name__)

# Predefined password
CORRECT_PASSWORD = "Surya@123"

# List of random success messages
SUCCESS_MESSAGES = [
    "Welcome, you have successfully logged in!",
    "Login successful! Have a great day!",
    "Access granted! Enjoy your time here!",
    "You are now logged in! Welcome aboard!"
]

@app.route('/', methods=['GET', 'POST'])
def login():
    if request.method == 'POST':
        username = request.form['username']
        password = request.form['password']

        if password == CORRECT_PASSWORD:
            message = random.choice(SUCCESS_MESSAGES)
            return render_template('success.html', username=username, message=message)
        else:
            return render_template('index.html', error="Invalid password. Try again.")

    return render_template('index.html')

if __name__ == '__main__':
    app.run(debug=True) 
