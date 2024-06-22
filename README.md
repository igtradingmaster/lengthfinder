
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Input Length Finder</title>
  <!-- Bootstrap CSS -->
  <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
  <!-- Custom CSS -->
  <style>
  body {
  background-color: #f8f9fa;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  position: relative;
  
}
body {
  background-image: url('https://cdn.wallpapersafari.com/9/40/VOTeQt.gif'); /* Replace 'background.jpg' with your image path */
  background-size: cover; /* Cover the entire background */
  background-position: center; /* Center the background image */
  background-repeat: no-repeat; /* Do not repeat the background image */
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  color: #333; /* Text color */
}

.container {
  max-width: 600px;
  margin: auto;
  background-color: #fff;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  position: relative; /* Ensure relative positioning for children */
}

h2 {
  text-align: center;
  color: #00060c;
}

.form-group {
  margin-bottom: 20px;
}

textarea {
  font-size: 16px;
  border: 1px solid #ced4da;
}

.btn-primary {
  background-color: #007bff;
  border-color: #007bff;
}

.btn-primary:hover {
  background-color: #0056b3;
  border-color: #0056b3;
}

#result {
  margin-top: 20px;
  border-top: 1px solid #ced4da;
  padding-top: 20px;
}

#result p {
  margin-bottom: 10px;
}

#result ul {
  list-style-type: none;
  padding: 0;
}

#result li {
  margin-bottom: 5px;
}

/* Styling for exit logo */
#exitLogo {
  position: absolute;
  top: 10px;
  right: 10px;
  width: 50px; /* Fixed width */
  height: 50px; /* Fixed height */
  display: flex;
  justify-content: center;
  align-items: center;
}

#exitLogo img {
  width: 100%;
  height: 100%;
  object-fit: contain; /* Maintain aspect ratio */
}
h1{
display:none;
}
  </style>
</head>
<body>
    <body>
        <div class="container">
          <h2 class="mt-4 mb-4">LENGTH FINDER</h2>
          <div class="form-group">
            <label for="inputText">Enter your text:</label>
            <textarea class="form-control" id="inputText" rows="5"></textarea>
          </div>
          <button class="btn btn-primary" onclick="analyzeInput()">Analyze</button>
      
          <div id="result" class="mt-4">
            <!-- Results will be displayed here -->
          </div>
      
          <!-- Exit logo link -->
          <a href="index.html" id="exitLogo">
            <img src="https://t3.ftcdn.net/jpg/04/51/52/52/360_F_451525222_IKqxMEeAVBS6Pj5JpJU0MxnQAtasHZPe.jpg" alt="">
          </a>
        </div>
      
        <!-- Bootstrap JS and dependencies -->
        <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
        <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.5.4/dist/umd/popper.min.js"></script>
        <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>
        
        <!-- Custom JavaScript -->
  <script>
    function analyzeInput() {
  // Get user input
  const userInput = document.getElementById('inputText').value;

  // Calculate length and character counts
  const length = userInput.length;
  const characterCount = {};
  const regex = /[a-zA-Z]/g;

  // Count occurrences of each letter
  userInput.toLowerCase().match(regex).forEach(letter => {
    if (characterCount[letter]) {
      characterCount[letter]++;
    } else {
      characterCount[letter] = 1;
    }
  });

  // Prepare output
  let output = `<p><strong>Length:</strong> ${length}</p>`;
  output += `<p><strong>Character Counts:</strong></p>`;
  output += `<ul>`;
  for (let char in characterCount) {
    output += `<li>${char}: ${characterCount[char]}</li>`;
  }
  output += `</ul>`;

  // Display results
  document.getElementById('result').innerHTML = output;
}

  </script>
</body>
