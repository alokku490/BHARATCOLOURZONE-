# BHARATCOLOURZONE-
Colour prediction website 
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>BHARATCOLOURZONE</title>
  <link href="style.css" rel="stylesheet" />
</head>
<body>
  <header>
    <h1>BHARATCOLOURZONE</h1>
    <div class="wallet">Wallet: ₹<span id="wallet">100</span></div>
    <button onclick="alert('Recharge coming soon')">Recharge</button>
  </header>
  <main>
    <div class="games">
      <a href="win-go.html" class="game-card">Win Go</a>
      <a href="5d.html" class="game-card">5D</a>
      <a href="trx.html" class="game-card">TRX</a>
      <a href="dragon.html" class="game-card">Dragon Tiger</a>
    </div>
  </main>
  <nav class="bottom-nav">
    <a href="index.html">Home</a>
    <a href="wallet.html">Wallet</a>
    <a href="history.html">History</a>
    <a href="account.html">Account</a>
  </nav>
</body>
</html>


body {
  font-family: 'Segoe UI', sans-serif;
  margin: 0;
  padding: 0;
  background: #121212;
  color: #fff;
}
header {
  background: linear-gradient(90deg, #ff4e50, #f9d423);
  color: white;
  padding: 20px;
  text-align: center;
}
.wallet {
  font-size: 18px;
  margin: 10px 0;
}
main {
  padding: 20px;
}
.games {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 20px;
}
.game-card {
  background: linear-gradient(135deg, #4facfe, #00f2fe);
  color: white;
  padding: 20px;
  border-radius: 12px;
  width: 40%;
  text-align: center;
  font-size: 18px;
  text-decoration: none;
  font-weight: bold;
}
.bottom-nav {
  position: fixed;
  bottom: 0;
  width: 100%;
  background: #1e1e1e;
  display: flex;
  justify-content: space-around;
  padding: 10px 0;
}
.bottom-nav a {
  color: white;
  text-decoration: none;
  font-size: 14px;
}



<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8" />
  <link href="style.css" rel="stylesheet" />
</head>
<body>
  <h2>Win Go Game</h2>
  <p>Coming soon...</p>
  <a href="index.html">Back</a>
</body>
</html>



<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8" />
  <link href="style.css" rel="stylesheet" />
</head>
<body>
  <h2>Wallet</h2>
  <p>Balance: ₹100</p>
  <a href="index.html">Back</a>
</body>
</html>



<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8" />
  <link href="style.css" rel="stylesheet" />
</head>
<body>
  <h2>History</h2>
  <p>No transactions yet.</p>
  <a href="index.html">Back</a>
</body>
</html>



<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8" />
  <link href="style.css" rel="stylesheet" />
</head>
<body>
  <h2>Account</h2>
  <p>UID: 123456789</p>
  <a href="index.html">Back</a>
</body>
</html>



<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>BharatColourZone - Admin Panel</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background: #101010;
      color: white;
      padding: 20px;
    }
    h1 { color: #ffca28; }
    .game-box {
      background: #1e1e1e;
      border-radius: 10px;
      padding: 15px;
      margin-bottom: 20px;
    }
    .game-box h2 {
      margin-top: 0;
    }
    label {
      display: block;
      margin-top: 10px;
    }
    select, input {
      padding: 5px;
      margin-top: 5px;
      width: 100%;
    }
    button {
      margin-top: 10px;
      padding: 8px 16px;
      font-weight: bold;
      background: #ff5722;
      border: none;
      color: white;
      cursor: pointer;
      border-radius: 5px;
    }
    .result {
      margin-top: 10px;
      color: #00e676;
    }
  </style>
</head>
<body>

  <h1>Admin Panel - BharatColourZone</h1>

  <div class="game-box" id="winGoBox">
    <h2>Win Go (Auto Mode)</h2>

    <label>Enter total user bets (in ₹):</label>
    <label>Red: <input type="number" id="redBet" value="0"></label>
    <label>Green: <input type="number" id="greenBet" value="0"></label>
    <label>Violet: <input type="number" id="violetBet" value="0"></label>

    <button onclick="calculateWinGoResult()">Calculate Safe Result</button>
    <div class="result" id="winGoResult">Result: -</div>
  </div>

  <script>
    function calculateWinGoResult() {
      // Step 1: Get all user bets
      const bets = {
        Red: parseInt(document.getElementById('redBet').value) || 0,
        Green: parseInt(document.getElementById('greenBet').value) || 0,
        Violet: parseInt(document.getElementById('violetBet').value) || 0
      };

      // Step 2: Find the key (color) with the lowest bet
      let lowest = Object.entries(bets).reduce((a, b) => a[1] < b[1] ? a : b);

      // Step 3: Set that as result
      const result = lowest[0];

      // Step 4: Show the result
      document.getElementById('winGoResult').innerText = `Result: ${result} (Lowest Bet = ₹${lowest[1]})`;

      // Step 5: (Optional) Send to backend or set in database
      // sendResultToDB("WinGo", result);
    }

    // Optional backend API call placeholder
    /*
    function sendResultToDB(game, result) {
      fetch('/api/set-result', {
        method: 'POST',
        headers: {'Content-Type': 'application/json'},
        body: JSON.stringify({ game, result })
      }).then(res => res.json())
        .then(data => alert("Result updated on server."))
        .catch(err => console.error(err));
    }
    */
  </script>

</body>
</html>
