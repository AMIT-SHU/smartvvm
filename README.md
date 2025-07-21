<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>SmartVVM - School Management System</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    :root {
      --main-color: #4a90e2;
      --accent-color: #ffffff;
      --background-color: #f4f6f8;
      --card-bg: #ffffff;
      --card-shadow: rgba(0, 0, 0, 0.1);
      --radius: 10px;
      --font: 'Segoe UI', sans-serif;
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: var(--font);
    }

    body {
      background-color: var(--background-color);
      color: #333;
      padding: 20px;
    }

    .login-container, .dashboard, .form-section {
      max-width: 500px;
      background: var(--card-bg);
      padding: 30px;
      margin: auto;
      border-radius: var(--radius);
      box-shadow: 0 4px 12px var(--card-shadow);
    }

    h2 {
      text-align: center;
      color: var(--main-color);
      margin-bottom: 20px;
    }

    input, select, button, textarea {
      width: 100%;
      padding: 12px;
      margin: 10px 0;
      border-radius: var(--radius);
      border: 1px solid #ccc;
    }

    button {
      background-color: var(--main-color);
      color: var(--accent-color);
      border: none;
      cursor: pointer;
      transition: background 0.3s ease;
    }

    button:hover {
      background-color: #3a78c2;
    }

    .hidden { display: none; }
    .lang-toggle {
      text-align: center;
      margin-bottom: 10px;
    }

    .dashboard-nav button {
      margin: 5px 0;
    }
  </style>
</head>
<body>

  <div class="login-container" id="login-box">
    <h2>Login</h2>
    <input type="text" id="username" placeholder="Username">
    <input type="password" id="password" placeholder="Password">
    <button onclick="login()">Login</button>
  </div>

  <div class="dashboard hidden" id="dashboard">
    <div class="lang-toggle">
      <button onclick="switchLang('en')">English</button>
      <button onclick="switchLang('hi')">हिंदी</button>
    </div>
    <h2 id="dashboard-title">Dashboard</h2>
    <div class="dashboard-nav">
      <button onclick="showSection('students')">👨‍🎓 Students</button>
      <button onclick="showSection('fees')">💸 Fees</button>
      <button onclick="showSection('attendance')">📊 Attendance</button>
      <button onclick="showSection('results')">📈 Results</button>
      <button onclick="logout()">🚪 Logout</button>
    </div>
  </div>

  <div class="form-section hidden" id="students">
    <h2>Student Registration</h2>
    <input placeholder="Full Name">
    <input placeholder="Class">
    <input placeholder="Roll Number">
    <input placeholder="Father's Name">
    <input placeholder="Mobile Number">
    <select>
      <option>Select Gender</option>
      <option>Male</option>
      <option>Female</option>
      <option>Other</option>
    </select>
    <button onclick="alert('Student Registered!')">Register</button>
  </div>

  <div class="form-section hidden" id="fees">
    <h2>Fees Payment</h2>
    <input placeholder="Student Name">
    <input placeholder="Class">
    <input placeholder="Amount">
    <input placeholder="Date">
    <button onclick="alert('Fees Submitted!')">Submit</button>
  </div>

  <div class="form-section hidden" id="attendance">
    <h2>Attendance</h2>
    <input placeholder="Student Name">
    <input placeholder="Class">
    <select>
      <option>Present</option>
      <option>Absent</option>
    </select>
    <input placeholder="Date">
    <button onclick="alert('Attendance Marked!')">Mark</button>
  </div>

  <div class="form-section hidden" id="results">
    <h2>Upload Result</h2>
    <input placeholder="Student Name">
    <input placeholder="Class">
    <input placeholder="Subject">
    <input placeholder="Marks">
    <button onclick="alert('Result Uploaded!')">Upload</button>
  </div>

  <script>
    function login() {
      const user = document.getElementById('username').value;
      const pass = document.getElementById('password').value;
      if (user === 'admin' && pass === '123456') {
        document.getElementById('login-box').classList.add('hidden');
        document.getElementById('dashboard').classList.remove('hidden');
      } else {
        alert('Invalid credentials!');
      }
    }

    function logout() {
      document.getElementById('dashboard').classList.add('hidden');
      document.getElementById('students').classList.add('hidden');
      document.getElementById('fees').classList.add('hidden');
      document.getElementById('attendance').classList.add('hidden');
      document.getElementById('results').classList.add('hidden');
      document.getElementById('login-box').classList.remove('hidden');
    }

    function showSection(id) {
      ['students', 'fees', 'attendance', 'results'].forEach(sec => {
        document.getElementById(sec).classList.add('hidden');
      });
      document.getElementById(id).classList.remove('hidden');
    }

    function switchLang(lang) {
      const titles = {
        en: {
          Dashboard: 'Dashboard',
          'Student Registration': 'Student Registration',
          'Fees Payment': 'Fees Payment',
          Attendance: 'Attendance',
          'Upload Result': 'Upload Result'
        },
        hi: {
          Dashboard: 'डैशबोर्ड',
          'Student Registration': 'छात्र पंजीकरण',
          'Fees Payment': 'फीस भुगतान',
          Attendance: 'उपस्थिति',
          'Upload Result': 'परिणाम अपलोड करें'
        }
      };
      const t = titles[lang];
      document.getElementById('dashboard-title').innerText = t['Dashboard'];
      document.querySelector("#students h2").innerText = t['Student Registration'];
      document.querySelector("#fees h2").innerText = t['Fees Payment'];
      document.querySelector("#attendance h2").innerText = t['Attendance'];
      document.querySelector("#results h2").innerText = t['Upload Result'];
    }
  </script>

</body>
</html>
