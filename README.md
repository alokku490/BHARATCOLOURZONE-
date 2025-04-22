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
  <h2>5D Game</h2>
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
  <h2>TRX Game</h2>
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
  <h2>Dragon Tiger Game</h2>
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
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Admin Panel - BharatColourZone</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background: #1c1c1c;
      color: white;
      padding: 20px;
    }
    h1 { color: #ffca28; }
    .game-section {
      background: #2a2a2a;
      padding: 15px;
      border-radius: 10px;
      margin: 15px 0;
    }
    .label {
      display: inline-block;
      width: 100px;
    }
    button {
      padding: 5px 15px;
      margin-left: 10px;
    }
  </style>
</head>
<body>
  <h1>Admin Panel - BharatColourZone</h1>
  <p>Use this panel to control WinGo, 5D, TRX, K3 results.</p>

  <div class="game-section">
    <h2>Win Go</h2>
    <div><span class="label">Mode:</span>
      <select id="winGoMode">
        <option value="auto">Auto</option>
        <option value="manual">Manual</option>
      </select>
    </div>
    <div><span class="label">Set Result:</span>
      <select id="winGoResult">
        <option value="Green">Green</option>
        <option value="Red">Red</option>
        <option value="Violet">Violet</option>
      </select>
      <button onclick="setGameResult('WinGo')">Apply</button>
    </div>
    <p id="winGoStatus">[Auto Mode Running]</p>
  </div>

  <div class="game-section">
    <h2>5D</h2>
    <div><span class="label">Mode:</span>
      <select id="fiveDMode">
        <option value="auto">Auto</option>
        <option value="manual">Manual</option>
      </select>
    </div>
    <div><span class="label">Set Number:</span>
      <input type="text" id="fiveDResult" maxlength="5" placeholder="e.g. 18325" />
      <button onclick="setGameResult('5D')">Apply</button>
    </div>
    <p id="fiveDStatus">[Auto Mode Running]</p>
  </div>

  <!-- More games can be added here like TRX, K3 in same format -->

  <script>
    function setGameResult(game) {
      let mode = document.getElementById(game === 'WinGo' ? 'winGoMode' : 'fiveDMode').value;
      let result = game === 'WinGo'
        ? document.getElementById('winGoResult').value
        : document.getElementById('fiveDResult').value;

      let status = document.getElementById(game === 'WinGo' ? 'winGoStatus' : 'fiveDStatus');
      if (mode === "manual") {
        status.innerText = `[Manual Mode] Result Set to ${result}`;
        // TODO: send to backend result = result
      } else {
        status.innerText = `[Auto Mode] Running safely...`;
        // Auto mode: simulate logic
        setInterval(() => {
          let safeResult = game === 'WinGo'
            ? ["Red", "Green", "Violet"][Math.floor(Math.random() * 3)]
            : String(Math.floor(Math.random() * 100000)).padStart(5, '0');
          status.innerText = `[Auto] Safe Result: ${safeResult}`;
        }, 60000); // every 60 seconds
      }
    }
  </script>
</body>
</html>



