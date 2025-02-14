<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ranjith & Sangeetha</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>❤️ Ranjith & Sangeetha ❤️</h1>
        <p>Forever in Love</p>
        <button onclick="startMusic()">Play Music 🎶</button>
    </div>

    <div class="quotes">
        <h2>Love Quotes</h2>
        <p>"You are the love of my life, my sunshine, my everything."</p>
        <p>"Every moment with you is like a beautiful dream come true."</p>
    </div>

    <div class="games">
        <h2>Love Games</h2>
        <a href="match-hearts.html">💖 Match the Hearts</a>
        <a href="love-quiz.html">❓ Love Quiz</a>
        <a href="jigsaw.html">🧩 Jigsaw Puzzle</a>
        <a href="word-search.html">🔎 Find the Name</a>
    </div>

    <audio id="bg-music" src="music.mp3" loop></audio>
    <script>
        function startMusic() {
            document.getElementById('bg-music').play();
        }
    </script>
</body>
</html>
body {
    font-family: Arial, sans-serif;
    text-align: center;
    background-color: pink;
    color: red;
}

.container {
    margin-top: 50px;
}

button {
    padding: 10px 20px;
    background-color: red;
    color: white;
    border: none;
    cursor: pointer;
}

.quotes, .games {
    margin-top: 30px;
}
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Match the Hearts</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <h1>💖 Match the Hearts 💖</h1>
    <div class="game-board" id="gameBoard"></div>

    <script>
        const emojis = ['❤️', '💖', '💕', '💘', '💞', '💓'];
        let cards = [...emojis, ...emojis].sort(() => Math.random() - 0.5);
        let firstCard, secondCard, lockBoard = false;

        function createBoard() {
            const board = document.getElementById('gameBoard');
            cards.forEach((emoji, index) => {
                let card = document.createElement('div');
                card.classList.add('card');
                card.dataset.emoji = emoji;
                card.innerHTML = '?';
                card.onclick = flipCard;
                board.appendChild(card);
            });
        }

        function flipCard() {
            if (lockBoard || this.innerHTML !== '?') return;
            this.innerHTML = this.dataset.emoji;
            if (!firstCard) {
                firstCard = this;
            } else {
                secondCard = this;
                checkMatch();
            }
        }

        function checkMatch() {
            lockBoard = true;
            if (firstCard.dataset.emoji === secondCard.dataset.emoji) {
                firstCard = secondCard = null;
                lockBoard = false;
            } else {
                setTimeout(() => {
                    firstCard.innerHTML = '?';
                    secondCard.innerHTML = '?';
                    firstCard = secondCard = null;
                    lockBoard = false;
                }, 1000);
            }
        }

        createBoard();
    </script>

    <style>
        .game-board {
            display: grid;
            grid-template-columns: repeat(4, 80px);
            gap: 10px;
            justify-content: center;
            margin-top: 20px;
        }
        .card {
            width: 80px;
            height: 80px;
            background: white;
            color: red;
            font-size: 30px;
            display: flex;
            align-items: center;
            justify-content: center;
            border: 2px solid red;
            cursor: pointer;
        }
    </style>
</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Love Quiz</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <h1>❓ Love Quiz ❓</h1>
    <div id="quiz"></div>
    <button onclick="checkAnswers()">Submit</button>
    <p id="result"></p>

    <script>
        const quizData = [
            { question: "What is the color of love?", options: ["Blue", "Red", "Green"], answer: "Red" },
            { question: "Which day is Valentine’s Day?", options: ["Feb 14", "March 14", "Dec 25"], answer: "Feb 14" },
            { question: "Who is the Greek god of love?", options: ["Ares", "Eros", "Zeus"], answer: "Eros" }
        ];

        function loadQuiz() {
            const quizDiv = document.getElementById("quiz");
            quizData.forEach((q, index) => {
                let questionHTML = `<p>${index + 1}. ${q.question}</p>`;
                q.options.forEach(option => {
                    questionHTML += `<input type="radio" name="q${index}" value="${option}"> ${option} `;
                });
                quizDiv.innerHTML += questionHTML + "<br>";
            });
        }

        function checkAnswers() {
            let score = 0;
            quizData.forEach((q, index) => {
                let selected = document.querySelector(`input[name="q${index}"]:checked`);
                if (selected && selected.value === q.answer) {
                    score++;
                }
            });
            document.getElementById("result").innerText = `Your Score: ${score} / ${quizData.length}`;
        }

        loadQuiz();
    </script>
</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Jigsaw Puzzle</title>
    <script src="https://cdn.jsdelivr.net/npm/puzzlejs@1.0.2/dist/puzzle.js"></script>
</head>
<body>
    <h1>🧩 Jigsaw Puzzle 🧩</h1>
    <canvas id="puzzleCanvas"></canvas>
    <script>
        const img = new Image();
        img.src = "your-photo.jpg"; // Replace with an actual image
        img.onload = () => {
            const puzzle = new Puzzle(img, document.getElementById('puzzleCanvas'), 3, 3);
            puzzle.init();
        };
    </script>
</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Find the Name</title>
</head>
<body>
    <h1>🔎 Find the Name 🔎</h1>
    <p>Find "Ranjith" and "Sangeetha" in the grid below.</p>
    <pre>
R   A   N   J   I   T   H   X
B   C   D   E   F   G   H   I
S   A   N   G   E   E   T   H
J   K   L   M   N   O   P   Q
    </pre>
</body>
</html>
