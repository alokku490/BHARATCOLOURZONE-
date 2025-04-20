# BHARATCOLOURZONE-
Colour prediction website 
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>BharatColourZone</title>
  <style>
    body { font-family: Arial, sans-serif; padding: 2rem; background: #f0f0f0; }
    .section { display: none; max-width: 400px; margin: auto; background: white; padding: 1.5rem; border-radius: 10px; box-shadow: 0 0 10px rgba(0,0,0,0.1); margin-bottom: 2rem; }
    input, button { width: 100%; margin: 0.5rem 0; padding: 0.6rem; }
    button { background-color: #007bff; color: white; border: none; cursor: pointer; }
    button:hover { background-color: #0056b3; }
    table { width: 100%; margin-top: 1rem; border-collapse: collapse; }
    table, th, td { border: 1px solid #ccc; }
    th, td { padding: 8px; text-align: center; }
    nav { text-align: center; margin-bottom: 1rem; }
    nav button { margin: 0 0.25rem; }
    .msg { text-align: center; color: red; font-weight: bold; }
  </style>
</head>
<body>

  <nav>
    <button onclick="showSection('home')">Home</button>
    <button onclick="showSection('login')">Login</button>
    <button onclick="showSection('signup')">Signup</button>
    <button onclick="showSection('admin')">Admin Panel</button>
  </nav>

  <div class="section" id="home">
    <h2>Welcome to BharatColourZone</h2>
    <p>This is a multi-game prediction platform for admin operations.</p>
  </div>

  <div class="section" id="login">
    <h2>Admin Login</h2>
    <input type="text" id="loginUser" placeholder="Username" />
    <input type="password" id="loginPass" placeholder="Password" />
    <button onclick="login()">Login</button>
    <p class="msg" id="loginMsg"></p>
  </div>

  <div class="section" id="signup">
    <h2>Admin Signup</h2>
    <input type="text" id="signupUser" placeholder="Username" />
    <input type="password" id="signupPass" placeholder="Password" />
    <button onclick="signup()">Signup</button>
    <p class="msg" id="signupMsg"></p>
  </div>

  <div class="section" id="admin">
    <h2>Admin Panel</h2>
    <button onclick="logout()">Logout</button>
    <h3>Add Result</h3>
    <input type="text" id="resultTime" placeholder="Time" />
    <input type="text" id="resultColor" placeholder="Color" />
    <button onclick="submitResult()">Submit</button>
    <p class="msg" id="adminMsg"></p>

    <h3>Live Results</h3>
    <table>
      <thead><tr><th>Time</th><th>Color</th></tr></thead>
      <tbody id="resultTable"></tbody>
    </table>
  </div>

  <script>
    const API = "https://your-deployment-url/api"; // Replace with actual backend URL

    function showSection(id) {
      document.querySelectorAll('.section').forEach(sec => sec.style.display = 'none');
      document.getElementById(id).style.display = 'block';
      if (id === 'admin') loadResults();
    }

    showSection('home');

    async function login() {
      const username = document.getElementById('loginUser').value;
      const password = document.getElementById('loginPass').value;
      const msg = document.getElementById('loginMsg');

      const res = await fetch(`${API}/admin/login`, {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({ username, password })
      });

      const data = await res.json();
      if (data.token) {
        localStorage.setItem('token', data.token);
        msg.textContent = "Login successful!";
        msg.style.color = 'green';
        showSection('admin');
      } else {
        msg.textContent = data.message || 'Login failed!';
      }
    }

    async function signup() {
      const username = document.getElementById('signupUser').value;
      const password = document.getElementById('signupPass').value;
      const msg = document.getElementById('signupMsg');

      const res = await fetch(`${API}/admin/signup`, {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({ username, password })
      });

      const data = await res.json();
      if (data.success) {
        msg.textContent = "Signup successful!";
        msg.style.color = 'green';
        setTimeout(() => showSection('login'), 1000);
      } else {
        msg.textContent = data.message || 'Signup failed!';
      }
    }

    async function submitResult() {
      const time = document.getElementById('resultTime').value;
      const color = document.getElementById('resultColor').value;
      const msg = document.getElementById('adminMsg');
      const token = localStorage.getItem('token');

      const res = await fetch(`${API}/add-result`, {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
          'Authorization': `Bearer ${token}`
        },
        body: JSON.stringify({ time, color })
      });

      const data = await res.json();
      msg.textContent = data.message || 'Result added!';
      msg.style.color = 'green';
      loadResults();
    }

    async function loadResults() {
      const res = await fetch(`${API}/results`);
      const data = await res.json();
      const table = document.getElementById('resultTable');
      table.innerHTML = '';
      data.forEach(item => {
        table.innerHTML += `<tr><td>${item.time}</td><td>${item.color}</td></tr>`;
      });
    }

    function logout() {
      localStorage.removeItem('token');
      showSection('login');
    }
  </script>
</body>
</html>
bharatcolourzone-backend/
│
├── server.js
├── package.json
├── .env (optional)
└── routes/
    └── admin.js
    {
  "name": "bharatcolourzone-backend",
  "version": "1.0.0",
  "main": "server.js",
  "scripts": {
    "start": "node server.js"
  },
  "dependencies": {
    "cors": "^2.8.5",
    "dotenv": "^16.0.3",
    "express": "^4.18.2",
    "jsonwebtoken": "^9.0.0",
    "mongoose": "^7.0.1"
  }
}
const express = require('express');
const cors = require('cors');
const mongoose = require('mongoose');
const adminRoutes = require('./routes/admin');

const app = express();
const PORT = process.env.PORT || 5000;

app.use(cors());
app.use(express.json());

mongoose.connect('mongodb+srv://<username>:<password>@cluster.mongodb.net/bharatdb?retryWrites=true&w=majority')
  .then(() => console.log("MongoDB connected"))
  .catch(err => console.error(err));

app.use('/api', adminRoutes);

app.get('/', (req, res) => res.send("BharatColourZone Backend Running"));

app.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
});
const express = require('express');
const jwt = require('jsonwebtoken');
const router = express.Router();

const SECRET = 'bharatcolourzone';

let users = [];
let results = [];

router.post('/admin/signup', (req, res) => {
  const { username, password } = req.body;
  if (users.find(u => u.username === username)) {
    return res.status(400).json({ message: 'User exists' });
  }
  users.push({ username, password });
  res.json({ success: true });
});

router.post('/admin/login', (req, res) => {
  const { username, password } = req.body;
  const user = users.find(u => u.username === username && u.password === password);
  if (!user) return res.status(401).json({ message: 'Invalid credentials' });

  const token = jwt.sign({ username }, SECRET, { expiresIn: '1h' });
  res.json({ token });
});

function authenticate(req, res, next) {
  const authHeader = req.headers['authorization'];
  const token = authHeader?.split(' ')[1];
  if (!token) return res.status(403).json({ message: 'No token provided' });

  jwt.verify(token, SECRET, (err, user) => {
    if (err) return res.status(401).json({ message: 'Invalid token' });
    req.user = user;
    next();
  });
}

router.post('/add-result', authenticate, (req, res) => {
  const { time, color } = req.body;
  results.unshift({ time, color });
  res.json({ message: 'Result added' });
});

router.get('/results', (req, res) => {
  res.json(results.slice(0, 20)); // Send latest 20 results
});

module.exports = router;
PORT=5000
MONGODB_URI=mongodb+srv://<username>:<password>@cluster.mongodb.net/bharatdb?retryWrites=true&w=majority
JWT_SECRET=bharatcolourzone
