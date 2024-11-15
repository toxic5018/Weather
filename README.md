<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="Toxic5018's Game Development Portfolio">
  <title>Toxic5018 Game Development Portfolio</title>

  <!-- Set the website icon -->
  <link rel="icon" href="https://toxic5018.github.io/website_icon.png" type="image/png">

  <!-- Font Link for 'Sen' -->
  <link href="https://fonts.googleapis.com/css2?family=Sen:wght@400;600&display=swap" rel="stylesheet">

  <!-- AdSense Script -->
  <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-2851265996786440"
     crossorigin="anonymous"></script>

  <!-- Theme Script: Detect System Theme (Dark/Light Mode) -->
  <script>
    const prefersDarkScheme = window.matchMedia("(prefers-color-scheme: dark)");
    const body = document.body;

    // Function to update the background based on the system theme
    function updateTheme() {
      if (prefersDarkScheme.matches) {
        body.style.backgroundColor = "#121212"; // Dark background
        body.style.color = "#fff"; // Light text color
      } else {
        body.style.backgroundColor = "#ffffff"; // Light background
        body.style.color = "#000"; // Dark text color
      }
    }

    // Apply the theme on page load
    updateTheme();

    // Listen for changes in system theme preference
    prefersDarkScheme.addEventListener("change", updateTheme);
  </script>

  <!-- CSS Style for Sen Font -->
  <style>
    body {
      font-family: 'Sen', sans-serif;
    }

    /* Apply Arial font to download links */
    a {
      font-family: Arial, sans-serif;
    }
  </style>
</head>
<body>

  <!-- Your page content goes here -->
  
  <!-- Example for including the rest of the content -->
  <h1>Welcome to My Game Development Portfolio!</h1>
  <p>Explore the games I’ve created.</p>
  
  <!-- The rest of your HTML content... -->

</body>
</html>
