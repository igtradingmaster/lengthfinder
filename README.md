
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
    }

    table {
      width: 80%;
      margin: 20px auto;
      border-collapse: collapse;
    }

    table, th, td {
      border: 1px solid #ddd;
    }

    th, td {
      padding: 12px;
      text-align: left;
    }

    th {
      background-color: #4caf50;
      color: white;
    }
  </style>
</head>
<body onload="displayUsers()">
  <div id="adminContainer">
    <h2>Admin Page - All Users</h2>
    <table>
      <thead>
        <tr>
          <th>User ID</th>
          <th>Mobile Number</th>
          <th>Name</th>
          <th>Password</th>
          <th>Backup Code</th>
          <th>Email</th>
        </tr>
      </thead>
      <tbody id="userTableBody"></tbody>
    </table>
  </div>

  <script>
    function displayUsers() {
      var users = JSON.parse(localStorage.getItem("users")) || [];
      var tableBody = document.getElementById("userTableBody");

      // Clear existing rows
      tableBody.innerHTML = "";

      // Populate the table with user data
      users.forEach(user => {
        var row = tableBody.insertRow();
        var cellUserId = row.insertCell(0);
        var cellMobileNumber = row.insertCell(1);
        var cellName = row.insertCell(2);
        var cellPassword = row.insertCell(3);
        var cellBackupCode = row.insertCell(4);
        var cellEmail = row.insertCell(5);

        cellUserId.innerHTML = user.userId;
        cellMobileNumber.innerHTML = user.mobileNumber;
        cellName.innerHTML = user.name;
        cellPassword.innerHTML = user.password;
        cellBackupCode.innerHTML = user.backupCode;
        cellEmail.innerHTML = user.email;
      });
    }
  </script>
</body>
</html>
