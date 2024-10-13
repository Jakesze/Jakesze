<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Rock Paper Scissors Game</title>
<style>
    body {
        font-family: Arial, sans-serif;
        text-align: center;
    }
    h1 {
        color: #333;
    }
    #choices {
        margin-top: 20px;
    }
</style>
</head>
<body>
    <h1>Rock Paper Scissors Game</h1>
    <div id="choices">
        <button id="rock">Rock</button>
        <button id="paper">Paper</button>
        <button id="scissors">Scissors</button>
    </div>
    <p id="result"></p>

    <script>
        const choices = document.querySelectorAll('#choices button');
        const resultText = document.getElementById('result');

        choices.forEach(choice => {
            choice.addEventListener('click', () => {
                const userChoice = choice.id;
                const computerChoice = getComputerChoice();
                const result = determineWinner(userChoice, computerChoice);
                resultText.innerText = `You chose ${userChoice}. Computer chose ${computerChoice}. ${result}`;
            });
        });

        function getComputerChoice() {
            const choices = ['rock', 'paper', 'scissors'];
            const randomIndex = Math.floor(Math.random() * 3);
            return choices[randomIndex];
        }

        function determineWinner(userChoice, computerChoice) {
            if (userChoice === computerChoice) {
                return "It's a tie!";
            } else if (
                (userChoice === 'rock' && computerChoice === 'scissors') ||
                (userChoice === 'paper' && computerChoice === 'rock') ||
                (userChoice === 'scissors' && computerChoice === 'paper')
            ) {
                return "You win!";
            } else {
                return "Computer wins!";
            }
        }
    </script>
</body>
</html>
