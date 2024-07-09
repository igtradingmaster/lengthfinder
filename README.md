
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Responsive Key Verification</title>
    <link rel="stylesheet" href="css/index.css">
</head>
<body>
    <div class="container">
        <img id="responsive-img" src="https://cdn.create.vista.com/api/media/small/411026842/stock-vector-logo-design-white-letter-letter-logo-design-initial-letter-linked" alt="Responsive Image">
        <div class="input-section">
            <input type="text" id="key-input" placeholder="Enter your key"><br>
            <button id="verify-btn">Verify</button>
            <div id="loader" class="loader" style="display:none;"></div>
            <p id="verification-msg"></p>
        </div>
    </div>

    <div id="popup" class="popup">
        <div class="popup-content">
            <p>Key Verified!</p>
            <button id="login-btn">Login</button>
        </div>
    </div>

    <script src="js/serviceWorker.min.js"></script>
</body>
</html>
<style>
    body {
    font-family: Arial, sans-serif;
    background-color: #f0f0f0;
    margin: 0;
    padding: 0;
}

.container {
    text-align: center;
    margin-top: 20%;
}

button {
    padding: 10px 20px;
    font-size: 16px;
    cursor: pointer;
}
/* General Styles */
body, html {
    margin: 0;
    padding: 0;
    font-family: 'Helvetica Neue', sans-serif;
    background: linear-gradient(45deg, #1a2a6c, #291313, #000000);
    background-size: 400% 400%;
    animation: gradientBackground 15s ease infinite;
    background-color: #f0f0f0;
}

@keyframes gradientBackground {
    0% { background-position: 0% 50%; }
    50% { background-position: 100% 50%; }
    100% { background-position: 0% 50%; }
}

.container {
    text-align: center;
    padding: 20px;
    color: #fff;
    text-shadow: 0 0 10px rgba(0,0,0,0.5);
}

#responsive-img {
    width: 100%;
    height: auto;
    max-width: 100%;
    box-shadow: 0 0 20px rgba(0, 0, 0, 0.5);
    border-radius: 10px;
    animation: imageShadowBlink 3s infinite;
}

@keyframes imageShadowBlink {
    0%, 100% { box-shadow: 0 0 20px rgba(0, 0, 0, 0.5); }
    50% { box-shadow: 0 0 30px rgba(255, 255, 255, 0.7); }
}

/* Input Section */
.input-section {
    margin-top: 20px;
}

.input-section input, .input-section button {
    padding: 15px;
    font-size: 18px;
    margin: 5px;
    border: none;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
    transition: transform 0.3s;
}

.input-section input {
    width: 200px;
}

.input-section button {
    background: linear-gradient(90deg, #ff8a00, #e52e71);
    color: #fff;
    cursor: pointer;
    position: relative;
    overflow: hidden;
}

.input-section button:hover {
    transform: scale(1.05);
}

.input-section button:before {
    content: '';
    position: absolute;
    top: -50%;
    left: -50%;
    width: 200%;
    height: 200%;
    background: rgba(255, 255, 255, 0.2);
    transform: rotate(45deg);
    transition: all 0.5s;
}

.input-section button:hover:before {
    top: -70%;
    left: -70%;
}

.input-section button .loader {
    border: 3px solid rgba(255, 255, 255, 0.3);
    border-radius: 50%;
    border-top: 3px solid #fff;
    width: 15px;
    height: 15px;
    animation: spin 2s linear infinite;
    display: inline-block;
    margin-left: 10px;
}

@keyframes spin {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg); }
}

/* Popup Styles */
.popup {
    display: none;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0,0,0,0.7);
    justify-content: center;
    align-items: center;
}

.popup-content {
    background-color: #fff;
    padding: 20px;
    border-radius: 10px;
    text-align: center;
    box-shadow: 0 0 30px rgba(0, 0, 0, 0.5);
    animation: popupOpen 0.5s ease;
}

@keyframes popupOpen {
    from { transform: scale(0.7); opacity: 0; }
    to { transform: scale(1); opacity: 1; }
}

.popup-content.verified {
    background: linear-gradient(45deg, #56ab2f, #a8e063);
    color: #fff;
}

.popup-content.invalid {
    background: linear-gradient(45deg, #000000, #ff416c);
    color: #fff;
}

/* Verified Styles */
.verified button {
    background: linear-gradient(50deg, #000300, #158352);
    color: #ffffff;
    box-shadow: none;
    text text-shadow: black;
    color-shadow: black;
}

.verified p {
    color: #000000;
    font-size: 24px;
}

/* Responsive Styles */
@media (max-width: 768px) {
    #responsive-img {
        content: url('tablet.jpg');
    }

    .input-section input {
        width: 150px;
    }
}

@media (max-width: 480px) {
    #responsive-img {
        content: url('mobile.jpg');
    }

    .input-section input {
        width: 120px;
    }
}
img{
    max-height: 250px;
    max-width: auto;
}
h1{
display: none;
}
</style>
<script>
    document.getElementById('verify-btn').addEventListener('click', function() {
    const keyInput = document.getElementById('key-input').value;
    const verifyBtn = document.getElementById('verify-btn');
    const loader = document.createElement('div');
    loader.classList.add('loader');
    const popup = document.getElementById('popup');
    const popupContent = popup.querySelector('.popup-content');
    
    // Array of predefined keys
    const keysArray = ['123456', 'abcdef', 'qwerty', 'key123', 'adminKey'];

    // Show loader inside the button
    verifyBtn.disabled = true;
    verifyBtn.textContent = 'Verifying';
    verifyBtn.appendChild(loader);

    setTimeout(() => {
        loader.remove();
        verifyBtn.disabled = false;
        verifyBtn.textContent = 'Verify';

        if (keysArray.includes(keyInput)) {
            // Show verified message in popup
            popupContent.classList.remove('invalid');
            popupContent.classList.add('verified');
            popupContent.innerHTML = '<p>Key Verified!</p><button id="login-btn">Login</button>';
            popup.style.display = 'flex';

            document.getElementById('login-btn').addEventListener('click', () => {
                // Redirect to the second page
                window.location.href = 'secondpage.html';
            });
        } else {
            // Show error message in popup
            popupContent.classList.remove('verified');
            popupContent.classList.add('invalid');
            popupContent.innerHTML = '<p>Invalid Key. Please try again.</p>';
            popup.style.display = 'flex';

            // Hide the popup after 4 seconds
            setTimeout(() => {
                popup.style.display = 'none';
            }, 41000);
        }
    }, 2000); // Simulate AJAX delay
});


</script>
