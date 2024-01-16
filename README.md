<!DOCTYPE html>
<html>
  <head>
    <title>My Dynamic Website</title>
    <style>
      body {
        font-family: Arial, sans-serif;
      }
      #content {
        margin: 0 auto;
        width: 80%;
      }
    </style>
  </head>
  <body>
    <div id="content">
      <h1>Welcome to my dynamic website!</h1>
      <p id="message"></p>
      <button id="loadButton">Load data</button>
    </div>

    <script>
      // This is a sample API endpoint that returns a random message
      const apiEndpoint = 'https://api.example.com/messages/random';

      // This function fetches data from the API and updates the message on the page
      async function loadData() {
        try {
          const response = await fetch(apiEndpoint);
          const data = await response.json();
          document.getElementById('message').innerText = data.message;
        } catch (error) {
          console.error('Error fetching data:', error);
          document.getElementById('message').innerText = 'An error occurred while loading data.';
        }
      }

      // This function adds a click event listener to the load button
      function init() {
        document.getElementById('loadButton').addEventListener('click', loadData);
      }

      // This line calls the init function when the page loads
      window.addEventListener('load', init);
    </script>
  </body>
</html>
