<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Admin Panel</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            padding: 0;
        }

        header {
            background-color: #333;
            color: white;
            text-align: center;
            padding: 1em;
        }

        section {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 80vh;
        }

        #admin-info {
            background-color: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            max-width: 400px;
            width: 100%;
            text-align: left;
        }
        .social-icon {
      width: 54px; /* Adjust the size as needed */
      height: 50px;
      margin: 10px;
      cursor: pointer;
    }
    button{
        background-color: #f4f4f4;
    }
    </style>
    <script>
        function redirectToAdminEmail() {
            // Replace the admin's email address with the actual email address
            var adminEmail = 'vedbhogayta7@gmail.com';
            window.location.href = 'mailto:' + adminEmail;
        }
        // Function to redirect to WhatsApp
    function redirectToWhatsApp() {
      window.location.href = 'https://api.whatsapp.com/send?phone=6353074867'; // Replace with your WhatsApp link
    }

    // Function to redirect to Instagram
    function redirectToInstagram() {
      window.location.href = 'https://www.instagram.com/_ved_bhogayta_/'; // Replace with your Instagram profile link
    }
    </script>
</head>
<body>

    <header>
        <h1>Contect To Admin</h1>
    </header>

    <section>
        <div id="admin-info">
            <h2>Admin Information</h2>
            <p><strong>Name:</strong> ved bhogayta</p>
            <p><strong>Email:</strong> <a href="javascript:void(0);" onclick="redirectToAdminEmail()">vedbhogayta7@gmail.com</a></p>
            <p><strong>Address:</strong> 45 Main St Road, City : Bhanvad , Zip Code : 360-510 (Gujarat).</p>
            <p><strong>Description:</strong> Full Website Hendelling ved bhogayta, Admin : ved bhogayta , Employee : Ved bhogayta , Thank you Team Igtradingmaster</p><ul></ul>
        <center><button><a href="payment.html">Click To Home</a></button></center>
        </div>
    </section>
<center><!-- WhatsApp Icon -->
<img class="social-icon" src="C:\Users\vedbh\OneDrive\Desktop\trading\images\whatshapp icon.png" alt="WhatsApp" onclick="redirectToWhatsApp()">

<!-- Instagram Icon -->
<img class="social-icon" src="C:\Users\vedbh\OneDrive\Desktop\trading\images\instagram icon.png" alt="Instagram" onclick="redirectToInstagram()">
</center>
</body>
</html>
