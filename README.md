
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f4f4f4;
      margin: 0;
      padding: 0;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }

    #adminContainer {
      text-align: center;
      padding: 20px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
      background-color: #fff;
      border-radius: 8px;
    }

    button {
      background-color: #4caf50;
      color: white;
      padding: 10px;
      border: none;
      border-radius: 4px;
      cursor: pointer;
      margin-top: 10px;
    }

    button:hover {
      background-color: #45a049;
    }

    table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 20px;
    }

    th, td {
      border: 1px solid #ddd;
      padding: 8px;
      text-align: left;
    }

    th {
      background-color: #4caf50;
      color: white;
    }
    </style>
  <script>
    // Your existing JavaScript functions here

    function showUserPage() {
      window.location.href = "https://igtradingmaster.github.io/LOGIN/";
    }

    function displayAllUsers() {
      // Retrieve all users from localStorage
      var users = JSON.parse(localStorage.getItem("users")) || [];

      // Display user data in a table
      var table = "<table><tr><th>User ID</th><th>Mobile Number</th><th>Name</th><th>Password</th><th>Backup Code</th><th>Email</th></tr>";

      for (var i = 0; i < users.length; i++) {
        table += "<tr><td>" + users[i].userId + "</td><td>" + users[i].mobileNumber + "</td><td>" + users[i].name + "</td><td>" + users[i].password + "</td><td>" + users[i].backupCode + "</td><td>" + users[i].email + "</td></tr>";
      }

      table += "</table>";

      // Display the table in the adminContainer
      document.getElementById("adminContainer").innerHTML = table;
    }
  </script>
</head>
<body>
  <div id="adminContainer">
    <h2>Admin Page</h2>
    <button onclick="showUserPage()">Back to User Page</button>
    <button onclick="displayAllUsers()">Display All Users</button>
  </div>
</body>
</html>
