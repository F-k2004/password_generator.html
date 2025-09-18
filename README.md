<!-- password_generator.html -->
<!DOCTYPE html>
<html lang="fa">
<head>
  <meta charset="UTF-8">
  <title>🔑 تولیدکننده پسورد قوی</title>
  <style>
    body {
      fon-family: sans-serif;
      background: linear-gradient(135deg, #84fab0, #8fd3f4);
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      text-align: center;
    }
    h1 {
      margin-bottom: 20px;
    }
    input[type=range] {
      width: 200px;
    }
    .password-box {
      background: #fff;
      padding: 10px 20px;
      border-radius: 10px;
      margin: 15px 0;
      font-weight: bold;
      font-size: 20px;
      min-width: 220px;
      word-break: break-all;
    }
    button {
      background: #333;
      color: #fff;
      border: none;
      padding: 10px 20px;
      border-radius: 8px;
      cursor: pointer;
      margin: 5px;
      transition: 0.3s;
    }
    button:hover {
      background: #555;
    }
  </style>
</head>
<body>
  <h1>🔑 تولید پسورد قوی</h1>

  <label>طول پسورد: <span id="lengthLabel">12</span></label><br>
  <input type="range" id="length" min="6" max="32" value="12" oninput="updateLength()"><br>

  <div class="password-box" id="password">اینجا نمایش داده می‌شود</div>

  <button onclick="generatePassword()">🔄 بساز</button>
  <button onclick="copyPassword()">📋 کپی</button>

  <script>
    function updateLength() {
      document.getElementById("lengthLabel").textContent = document.getElementById("length").value;
    }

    function generatePassword() {
      const length = document.getElementById("length").value;
      const chars = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789!@#$%^&*()_+";
      let password = "";
      for (let i = 0; i < length; i++) {
        password += chars.charAt(Math.floor(Math.random() * chars.length));
      }
      document.getElementById("password").textContent = password;
    }

    function copyPassword() {
      const password = document.getElementById("password").textContent;
      navigator.clipboard.writeText(password).then(() => {
        alert("✅ پسورد کپی شد!");
      });
    }
  </script>
</body>
</html>
