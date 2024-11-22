# PRODIGY_WD_02
<!----- html code----->
<!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Responsive Stopwatch</title>
        <link rel="stylesheet" href="styles.css">
    </head>
    <body>
        <div class="container">
            <h1>Stopwatch</h1>
            <div class="stopwatch">
                <div id="display">00:00:00</div>
                <div class="controls">
                    <button id="start" onclick="startStopwatch()">Start</button>
                    <button id="stop" onclick="stopStopwatch()" disabled>Stop</button>
                    <button id="reset" onclick="resetStopwatch()" disabled>Reset</button>
                </div>
            </div>
        </div>
        <script src="script.js"></script>
    </body>
    </html>
    <!------------css code------->
    * {
    box-sizing: border-box;
}

body {
    font-family: Arial, sans-serif;
    background-color: #0d0d0e;
    margin: 0;
    padding: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
}

.container {
    text-align: center;
    background: white;
    padding: 30px;
    border-radius: 50px;
    box-shadow: 0 2px 10px rgba(14, 35, 63, 0.1);
    width: 400px;
}

h1 {
    margin-bottom: 50px;
}

.stopwatch {
    font-size: 3ex;
    margin-bottom: 40px;
    padding: 20px;
    background-color: #5f98b9;
    border-radius: 20px;
}

.controls button {
    padding: 10px 20px;
    margin: 5px;
    border: none;
    border-radius: 10px;
    cursor: pointer;
    font-size: 1em;
    transition: background 0.3s;
}

.controls button:hover {
    background-color: #09111a;
    color: rgb(84, 147, 219);
}

.controls button:disabled {
    background-color: #ccc;
    cursor: not-allowed;
}
<!----------javascript-------->
let timer;
let isRunning = false;
let elapsedTime = 0;

function startStopwatch() {
    if (!isRunning) {
        isRunning = true;
        document.getElementById("start").disabled = true;
        document.getElementById("stop").disabled = false;
        document.getElementById("reset").disabled = false;

        timer = setInterval(() => {
            elapsedTime++;
            displayTime();
        }, 1000);
    }
}

function stopStopwatch() {
    if (isRunning) {
        clearInterval(timer);
        isRunning = false;
        document.getElementById("start").disabled = false;
        document.getElementById("stop").disabled = true;
    }
}

function resetStopwatch() {
    clearInterval(timer);
    isRunning = false;
    elapsedTime = 0;
    displayTime();
    document.getElementById("start").disabled = false;
    document.getElementById("stop").disabled = true;
    document.getElementById("reset").disabled = true;
}

function displayTime() {
    const hours = Math.floor(elapsedTime / 3600);
    const minutes = Math.floor((elapsedTime % 3600) / 60);
    const seconds = elapsedTime % 60;

    document.getElementById("display").textContent = 
        String(hours).padStart(2, '0') + ':' + 
        String(minutes).padStart(2, '0') + ':' + 
        String(seconds).padStart(2, '0');
}

    

