<!DOCTYPE html>
<html lang="de">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Meine Spiele-Website</title>
  <style>
    body { font-family: Arial, sans-serif; margin: 0; background: #f0f0f0; color: #333; }
    header { background: #4a90e2; color: white; padding: 20px; text-align: center; }
    main { padding: 20px; max-width: 800px; margin: auto; }
    .game-card { background: white; padding: 20px; border-radius: 10px; box-shadow: 0 4px 10px rgba(0,0,0,0.1); margin-bottom: 20px; }
    button { padding: 10px 15px; border: none; border-radius: 5px; background: #4a90e2; color: white; cursor: pointer; font-size: 16px; }
    button:hover { background: #357abd; }
  </style>
</head>
<body>
  <header>
    <h1>Willkommen auf meiner Spiele-Website</h1>
    <p>Spiele direkt im Browser 🚀</p>
  </header>

  <main>
    <!-- Tic-Tac-Toe -->
    <div class="game-card">
      <h2>Tic-Tac-Toe</h2>
      <div id="ticTacToeBoard" style="display:grid; grid-template-columns: repeat(3, 60px); grid-gap:5px;"></div>
      <button onclick="startTicTacToe()">Neues Spiel</button>
    </div>

    <!-- Zahlenraten -->
    <div class="game-card">
      <h2>Zahlenraten</h2>
      <p>Rate eine Zahl zwischen 1 und 10:</p>
      <input type="number" id="guessInput" min="1" max="10">
      <button onclick="checkGuess()">Raten</button>
      <p id="guessResult"></p>
    </div>

    <!-- Quiz -->
    <div class="game-card">
      <h2>Quiz</h2>
      <p>Was ist 2 + 2?</p>
      <button onclick="checkQuiz(4)">4</button>
      <button onclick="checkQuiz(5)">5</button>
      <p id="quizResult"></p>
    </div>
  </main>

  <footer>
    © 2026 Meine Spiele-Website
  </footer>

  <script>
    // Tic-Tac-Toe
    let ticTacToeBoard = [];
    let currentPlayer = 'X';
    function startTicTacToe() {
      ticTacToeBoard = ['', '', '', '', '', '', '', '', ''];
      currentPlayer = 'X';
      const boardDiv = document.getElementById('ticTacToeBoard');
      boardDiv.innerHTML = '';
      for(let i=0; i<9; i++) {
        const cell = document.createElement('button');
        cell.style.width = '60px';
        cell.style.height = '60px';
        cell.style.fontSize = '24px';
        cell.onclick = () => { if(cell.textContent===''){ cell.textContent=currentPlayer; ticTacToeBoard[i]=currentPlayer; currentPlayer = currentPlayer==='X'?'O':'X'; } };
        boardDiv.appendChild(cell);
      }
    }

    // Zahlenraten
    let randomNumber = Math.floor(Math.random()*10)+1;
    function checkGuess() {
      const guess = parseInt(document.getElementById('guessInput').value);
      const result = document.getElementById('guessResult');
      if(guess===randomNumber){
        result.textContent='Richtig! 🎉';
        randomNumber = Math.floor(Math.random()*10)+1;
      } else {
        result.textContent='Falsch, versuche es nochmal 😅';
      }
    }

    // Quiz
    function checkQuiz(answer){
      const result = document.getElementById('quizResult');
      if(answer===4){ result.textContent='Richtig! 🎉'; }
      else{ result.textContent='Falsch 😅'; }
    }
  </script>
</body>
</html>
