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
