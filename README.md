<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BankNifty Miner Tool</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 20px;
            background-color: #f4f4f4;
        }
        .container {
            max-width: 600px;
            margin: auto;
            background: white;
            padding: 20px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
        }
        input[type="number"], input[type="submit"] {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            box-sizing: border-box;
        }
        .result {
            margin-top: 20px;
            padding: 10px;
            background-color: #e7f3fe;
            border: 1px solid #b3e5fc;
            color: #0277bd;
        }
    </style>
</head>
<body>
    <div class="container">
        <h2>BankNifty Miner Tool</h2>
        <form id="bankniftyForm">
            <label for="entryPrice">Entry Price:</label>
            <input type="number" id="entryPrice" placeholder="Enter Entry Price">

            <label for="stopLoss">Stop Loss:</label>
            <input type="number" id="stopLoss" placeholder="Enter Stop Loss">

            <label for="targetPoints">Target Points:</label>
            <input type="number" id="targetPoints" placeholder="Enter Target Points (e.g., 400)">

            <input type="submit" value="Calculate">
        </form>

        <div class="result" id="result"></div>
    </div>

    <script>
        document.getElementById('bankniftyForm').addEventListener('submit', function(event) {
            event.preventDefault();

            const entryPrice = parseFloat(document.getElementById('entryPrice').value);
            const stopLoss = parseFloat(document.getElementById('stopLoss').value);
            const targetPoints = parseFloat(document.getElementById('targetPoints').value);

            if (isNaN(entryPrice) || isNaN(stopLoss) || isNaN(targetPoints)) {
                alert("Please enter valid numbers.");
                return;
            }

            const targetPrice = entryPrice + targetPoints;
            const resistance = targetPrice + (targetPoints * 0.005); // Adjust resistance
            const support = entryPrice - (entryPrice * 0.005); // Adjust support

            const resultDiv = document.getElementById('result');
            resultDiv.innerHTML = `
                <strong>Target Price:</strong> ${targetPrice.toFixed(2)}<br>
                <strong>Resistance Level:</strong> ${resistance.toFixed(2)}<br>
                <strong>Support Level:</strong> ${support.toFixed(2)}
            `;
        });
    </script>
</body>
</html>
