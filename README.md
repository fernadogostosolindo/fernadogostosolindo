<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Jogo de Adivinhação de Palavras</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="game-container">
        <h1>Jogo de Adivinhação de Palavras</h1>
        <p id="hint">Dica: _ _ _ _ _</p>
        <input type="text" id="guess" placeholder="Digite uma letra ou palavra">
        <button onclick="checkGuess()">Tentar</button>
        <p id="message"></p>
        <p id="tries">Tentativas restantes: 6</p>
        <div id="game-over" class="hidden">
            <p>Fim de jogo! A palavra era: <span id="final-word"></span></p>
            <button onclick="startGame()">Reiniciar</button>
        </div>
    </div>
    <script src="script.js"></script>
</body>
</html>
2. CSS (style.css)
css
Copiar
body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
}

.game-container {
    background-color: #fff;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
    text-align: center;
    width: 300px;
}

#hint {
    font-size: 24px;
    margin-bottom: 20px;
}

#guess {
    padding: 8px;
    font-size: 18px;
    margin-right: 10px;
    width: 50%;
}

button {
    padding: 10px 20px;
    font-size: 18px;
    cursor: pointer;
}

#message {
    font-size: 18px;
    color: #d9534f;
}

#tries {
    font-size: 18px;
}

.hidden {
    display: none;
}

body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
}

.game-container {
    background-color: #fff;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
    text-align: center;
    width: 300px;
}

#hint {
    font-size: 24px;
    margin-bottom: 20px;
}

#guess {
    padding: 8px;
    font-size: 18px;
    margin-right: 10px;
    width: 50%;
}

button {
    padding: 10px 20px;
    font-size: 18px;
    cursor: pointer;
}

#message {
    font-size: 18px;
    color: #d9534f;
}

#tries {
    font-size: 18px;
}

.hidden {
    display: none;
}let secretWord = "javascript";
let guessedLetters = [];
let tries = 6;

function startGame() {
    secretWord = "javascript";
    guessedLetters = [];
    tries = 6;
    document.getElementById("tries").textContent = "Tentativas restantes: " + tries;
    document.getElementById("message").textContent = "";
    document.getElementById("hint").textContent = "Dica: " + getHint();
    document.getElementById("game-over").classList.add("hidden");
    document.getElementById("guess").value = "";
}

function getHint() {
    let hint = "";
    for (let i = 0; i < secretWord.length; i++) {
        if (guessedLetters.includes(secretWord[i])) {
            hint += secretWord[i] + " ";
        } else {
            hint += "_ ";
        }
    }
    return hint.trim();
}

function checkGuess() {
    let guess = document.getElementById("guess").value.toLowerCase();
    document.getElementById("guess").value = "";

    if (guess.length === 1) { // Tentativa de letra
        if (secretWord.includes(guess)) {
            guessedLetters.push(guess);
            document.getElementById("message").textContent = "Boa! Você acertou uma letra!";
        } else {
            tries--;
            document.getElementById("tries").textContent = "Tentativas restantes: " + tries;
            document.getElementById("message").textContent = "Ops, tente novamente!";
        }
    } else if (guess === secretWord) { // Tentativa de palavra inteira
        document.getElementById("message").textContent = "Parabéns, você adivinhou a palavra!";
        guessedLetters = secretWord.split("");
    } else {
        tries--;
        document.getElementById("tries").textContent = "Tentativas restantes: " + tries;
        document.getElementById("message").textContent = "Tente novamente!";
    }

    document.getElementById("hint").textContent = "Dica: " + getHint();

    if (tries <= 0) {
        gameOver();
    }
}

function gameOver() {
    document.getElementById("game-over").classList.remove("hidden");
    document.getElementById("final-word").textContent = secretWord;
}

startGame();
