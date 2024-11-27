<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Crypto P&L Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        form {
            max-width: 300px;
        }
        label {
            display: block;
            margin-top: 10px;
        }
        input {
            width: 100%;
            padding: 5px;
            margin-top: 5px;
        }
        button {
            margin-top: 15px;
            padding: 10px;
        }
        #results {
            margin-top: 20px;
            border-top: 1px solid #ccc;
            padding-top: 10px;
        }
    </style>
</head>
<body>
    <h1>Cryptocurrency Profit & Loss Calculator</h1>
    <form id="calc-form">
        <label for="purchasePrice">Purchase Price:</label>
        <input type="number" id="purchasePrice" placeholder="e.g., 50000" required>

        <label for="currentPrice">Current Price:</label>
        <input type="number" id="currentPrice" placeholder="e.g., 60000" required>

        <label for="quantity">Quantity Owned (Optional):</label>
        <input type="number" id="quantity" placeholder="e.g., 1" value="1">

        <button type="button" id="calculateBtn">Calculate</button>
        <button type="reset">Reset</button>
    </form>

    <div id="results" style="display:none;">
        <h2>Results</h2>
        <p>Profit/Loss: <span id="profitLoss"></span></p>
        <p>ROI (%): <span id="roi"></span></p>
    </div>

    <script>
        document.getElementById("calculateBtn").addEventListener("click", function () {
            const purchasePrice = parseFloat(document.getElementById("purchasePrice").value);
            const currentPrice = parseFloat(document.getElementById("currentPrice").value);
            const quantity = parseFloat(document.getElementById("quantity").value) || 1;

            if (!purchasePrice || !currentPrice) {
                alert("Please enter valid purchase and current prices.");
                return;
            }

            // Calculate profit/loss and ROI
            const profitLoss = (currentPrice - purchasePrice) * quantity;
            const roi = ((currentPrice - purchasePrice) / purchasePrice) * 100;

            // Display results
            document.getElementById("profitLoss").textContent = profitLoss.toFixed(2);
            document.getElementById("roi").textContent = roi.toFixed(2) + "%";
            document.getElementById("results").style.display = "block";
        });
    </script>
</body>
</html>
