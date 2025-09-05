<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Age Calculator</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      padding: 20px;
      background: #f5f5f5;
    }
    .container {
      background: white;
      padding: 20px;
      border-radius: 15px;
      box-shadow: 0px 4px 10px rgba(0,0,0,0.2);
      max-width: 400px;
      margin: auto;
    }
    input {
      padding: 10px;
      margin: 10px;
      width: 80%;
      border-radius: 8px;
      border: 1px solid #ccc;
    }
    button {
      padding: 10px 20px;
      border: none;
      background: #4CAF50;
      color: white;
      border-radius: 8px;
      cursor: pointer;
    }
    button:hover {
      background: #45a049;
    }
    #result {
      margin-top: 15px;
      font-size: 18px;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <div class="container">
    <h2>📅 Age Calculator</h2>
    <input type="date" id="dob">
    <br>
    <button onclick="calculateAge()">Calculate Age</button>
    <p id="result"></p>
  </div>

  <script>
    function calculateAge() {
      const dob = document.getElementById("dob").value;
      if (!dob) {
        document.getElementById("result").innerText = "Please select your date of birth.";
        return;
      }

      const dobDate = new Date(dob);
      const today = new Date();

      let ageYears = today.getFullYear() - dobDate.getFullYear();
      let ageMonths = today.getMonth() - dobDate.getMonth();
      let ageDays = today.getDate() - dobDate.getDate();

      if (ageDays < 0) {
        ageMonths--;
        ageDays += new Date(today.getFullYear(), today.getMonth(), 0).getDate();
      }
      if (ageMonths < 0) {
        ageYears--;
        ageMonths += 12;
      }

      document.getElementById("result").innerText = 
        `You are ${ageYears} years, ${ageMonths} months, and ${ageDays} days old.`;
    }
  </script>
</body>
</html>
