# Modern-Calculator
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Modern Calculator</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="calculator">
        <div class="display">
            <input type="text" id="result" readonly placeholder="0">
        </div>
        <div class="buttons">
            <button class="btn operator" onclick="clearDisplay()">C</button>
            <button class="btn operator" onclick="deleteLast()">DEL</button>
            <button class="btn operator" onclick="appendValue('%')">%</button>
            <button class="btn operator" onclick="appendValue('/')">/</button>

            <button class="btn" onclick="appendValue('7')">7</button>
            <button class="btn" onclick="appendValue('8')">8</button>
            <button class="btn" onclick="appendValue('9')">9</button>
            <button class="btn operator" onclick="appendValue('*')">*</button>

            <button class="btn" onclick="appendValue('4')">4</button>
            <button class="btn" onclick="appendValue('5')">5</button>
            <button class="btn" onclick="appendValue('6')">6</button>
            <button class="btn operator" onclick="appendValue('-')">-</button>

            <button class="btn" onclick="appendValue('1')">1</button>
            <button class="btn" onclick="appendValue('2')">2</button>
            <button class="btn" onclick="appendValue('3')">3</button>
            <button class="btn operator" onclick="appendValue('+')">+</button>

            <button class="btn" onclick="appendValue('00')">00</button>
            <button class="btn" onclick="appendValue('0')">0</button>
            <button class="btn" onclick="appendValue('.')">.</button>
            <button class="btn equal" onclick="calculate()">=</button>
        </div>
    </div>
    <script src="script.js"></script>
</body>
</html>


* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

body {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    background: linear-gradient(135deg, #1e1e2f, #252542);
}

.calculator {
    background-color: #121214;
    padding: 25px;
    border-radius: 30px;
    box-shadow: 0 20px 50px rgba(0, 0, 0, 0.4);
    width: 350px;
}

.display {
    margin-bottom: 25px;
}

#result {
    width: 100%;
    height: 80px;
    background-color: #1a1a1e;
    border: none;
    outline: none;
    border-radius: 15px;
    color: #ffffff;
    font-size: 2.5rem;
    text-align: right;
    padding: 15px;
    font-weight: 300;
}

.buttons {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 12px;
}

.btn {
    padding: 20px;
    font-size: 1.3rem;
    border: none;
    outline: none;
    border-radius: 16px;
    background-color: #2d2d34;
    color: #ffffff;
    cursor: pointer;
    transition: all 0.2s ease;
}

.btn:active {
    transform: scale(0.95);
}

.btn:hover {
    background-color: #3e3e46;
}

.operator {
    color: #00adb5;
    font-weight: bold;
    background-color: #222831;
}

.operator:hover {
    background-color: #2d343f;
}

.equal {
    background: linear-gradient(135deg, #00adb5, #007a80);
    color: white;
    font-weight: bold;
    grid-row: span 1;
}

.equal:hover {
    background: linear-gradient(135deg, #00cfda, #00adb5);
}


const display = document.getElementById('result');

function appendValue(value) {
    if (display.value === 'Error') {
        display.value = '';
    }
    display.value += value;
}

function clearDisplay() {
    display.value = '';
}

function deleteLast() {
    display.value = display.value.slice(0, -1);
}

function calculate() {
    try {
        // eval() ব্যবহার করে সহজে হিসাব করা হয়েছে
        if (display.value !== "") {
            display.value = eval(display.value);
        }
    } catch (error) {
        display.value = 'Error';
    }
}

