
<html lang="en">
<head>
<meta charset="UTF-8">
<title>For My Special Someone ❤️</title>
<style>
    body {
        margin: 0;
        padding: 0;
        background: linear-gradient(135deg, #ff758c, #ff7eb3);
        font-family: 'Segoe UI', sans-serif;
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        overflow: hidden;
        text-align: center;
        color: white;
    }

    .container {
        background: rgba(255, 255, 255, 0.15);
        padding: 40px;
        border-radius: 20px;
        backdrop-filter: blur(10px);
        width: 380px;
        box-shadow: 0 10px 30px rgba(0,0,0,0.3);
    }

    h2 {
        min-height: 60px;
    }

    button {
        padding: 10px 20px;
        margin: 8px;
        border: none;
        border-radius: 20px;
        background: white;
        color: #ff4b7d;
        font-weight: bold;
        cursor: pointer;
        transition: 0.3s;
    }

    button:hover {
        background: #ff4b7d;
        color: white;
    }

    .heart {
        position: absolute;
        bottom: -20px;
        font-size: 20px;
        animation: floatUp 6s linear infinite;
    }

    @keyframes floatUp {
        0% { transform: translateY(0); opacity: 1; }
        100% { transform: translateY(-100vh); opacity: 0; }
    }
</style>
</head>
<body>

<div class="container" id="box">
    <h2 id="text"></h2>
    <div id="buttons"></div>
</div>

<script>
    const textElement = document.getElementById("text");
    const buttonsDiv = document.getElementById("buttons");
    let yesSize = 1;

    function typeText(text, callback) {
        textElement.innerHTML = "";
        let i = 0;
        const speed = 40;

        function typing() {
            if (i < text.length) {
                textElement.innerHTML += text.charAt(i);
                i++;
                setTimeout(typing, speed);
            } else if (callback) {
                callback();
            }
        }

        typing();
    }

    function firstQuestion() {
        typeText("Hi beautiful ❤️ How was your day?", () => {
            buttonsDiv.innerHTML = `
                <button onclick="secondQuestion()">Good 😊</button>
                <button onclick="secondQuestion()">Bad 😔</button>
            `;
        });
    }

    function secondQuestion() {
        buttonsDiv.innerHTML = "";
        typeText("No matter what happened today... I hope you know you're amazing 💕 How are you feeling?", () => {
            buttonsDiv.innerHTML = `
                <button onclick="thirdQuestion()">Happy 😄</button>
                <button onclick="thirdQuestion()">Tired 😴</button>
                <button onclick="thirdQuestion()">Stressed 😣</button>
            `;
        });
    }

    function thirdQuestion() {
        buttonsDiv.innerHTML = "";
        typeText("Whatever you’re feeling… I care about you more than you know 💖", () => {
            buttonsDiv.innerHTML = `
                <button onclick="finalQuestion()">Continue 💌</button>
            `;
        });
    }

    function finalQuestion() {
        buttonsDiv.innerHTML = "";
        typeText("You make my heart smile every single day... So I have something important to ask you 💘", () => {
            buttonsDiv.innerHTML = `
                <button onclick="bigQuestion()">I'm listening 👀</button>
            `;
        });
    }

    function bigQuestion() {
        buttonsDiv.innerHTML = "";
        typeText("Will you be my Valentine? ❤️", () => {
            buttonsDiv.innerHTML = `
                <button id="yesBtn" onmouseover="growYes(this)" onclick="yesAnswer()">YES!!! ❤️</button>
                <button onmouseover="moveNo(this)">No 🙈</button>
            `;
        });
    }

    function growYes(button) {
        yesSize += 0.2;
        button.style.transform = "scale(" + yesSize + ")";
    }

    function yesAnswer() {
        buttonsDiv.innerHTML = "";
        typeText("YAYYYYY 🥰❤️ You just made me the happiest person alive! I can't wait to spend Valentine's Day with you 💞");
    }

    function moveNo(button) {
        button.style.position = "absolute";
        button.style.left = Math.random() * 80 + "%";
        button.style.top = Math.random() * 80 + "%";
    }

    function createHeart() {
        const heart = document.createElement("div");
        heart.classList.add("heart");
        heart.innerHTML = "❤️";
        heart.style.left = Math.random() * 100 + "vw";
        document.body.appendChild(heart);

        setTimeout(() => {
            heart.remove();
        }, 6000);
    }

    setInterval(createHeart, 400);

    // Start
    firstQuestion();
</script>

</body>
</html>
