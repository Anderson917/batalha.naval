# batalha.naval<!DOCTYPE html>
<html>
  <head>
    <title>Hello, World!</title>
    <link rel="stylesheet" href="styles.css" />
  </head>
  <body>
      <h1 class="title">Hello World! </h1>
      <p id="currentTime"></p>
      <script src="script.js"></script>
  </body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Batalha Naval</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            margin: 0;
            background-color: #f0f0f0;
        }
        h1 {
            color: #333;
        }
        table {
            border-collapse: collapse;
        }
        td {
            width: 50px;
            height: 50px;
            text-align: center;
            vertical-align: middle;
            border: 1px solid #333;
            cursor: pointer;
        }
        .hit {
            background-color: red;
        }
        .miss {
            background-color: blue;
        }
    </style>
</head>
<body>
    <h1>Batalha Naval</h1>
    <table id="gameBoard"></table>
    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const boardSize = 5;
            let shipRow, shipCol;

            function initializeBoard() {
                const board = document.getElementById('gameBoard');
                for (let i = 0; i < boardSize; i++) {
                    const row = document.createElement('tr');
                    for (let j = 0; j < boardSize; j++) {
                        const cell = document.createElement('td');
                        cell.addEventListener('click', () => handleCellClick(i, j, cell));
                        row.appendChild(cell);
                    }
                    board.appendChild(row);
                }
                placeShip();
            }

            function placeShip() {
                shipRow = Math.floor(Math.random() * boardSize);
                shipCol = Math.floor(Math.random() * boardSize);
                console.log(`Ship is at (${shipRow}, ${shipCol})`); // Para fins de depuração
            }

            function handleCellClick(row, col, cell) {
                if (row === shipRow && col === shipCol) {
                    cell.classList.add('hit');
                    alert('Você afundou meu navio!');
                    resetGame();
                } else {
                    cell.classList.add('miss');
                }
            }

            function resetGame() {
                const board = document.getElementById('gameBoard');
                board.innerHTML = '';
                initializeBoard();
            }

            initializeBoard();
        });
    </script>
</body>
</html>
