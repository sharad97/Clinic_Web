<style>
html { height: 100% }
body { height: 100%; margin: 0; padding: 0 }

* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: Arial;
}

.header {
  text-align: center;
  padding: 32px;
}

.row {
  display: -ms-flexbox; /* IE10 */
  display: flex;
  -ms-flex-wrap: wrap; /* IE10 */
  flex-wrap: wrap;
  padding: 0 4px;
}

/* Create four equal columns that sits next to each other */
.column {
  -ms-flex: 25%; /* IE10 */
  flex: 25%;
  max-width: 25%;
  padding: 0 4px;
}

.column img {
  margin-top: 8px;
  vertical-align: middle;
  width: 100%;
}

/* Responsive layout - makes a two column-layout instead of four columns */
@media screen and (max-width: 800px) {
  .column {
    -ms-flex: 50%;
    flex: 50%;
    max-width: 50%;
  }
}

/* Responsive layout - makes the two columns stack on top of each other instead of next to each other */
@media screen and (max-width: 600px) {
  .column {
    -ms-flex: 100%;
    flex: 100%;
    max-width: 100%;
  }
}

.row_2 {
  display: -ms-flexbox; /* IE10 */
  display: flex;
  -ms-flex-wrap: wrap; /* IE10 */
  flex-wrap: wrap;
  padding: 0 4px;
}

.column_2 {
  -ms-flex: 50%;
  flex: 50%;
  max-width: 50%;
}

.column_2 img {
  margin-top: 8px;
  vertical-align: middle;
  width: 100%;
}

/* Responsive layout - makes a two column-layout instead of four columns */
@media screen and (max-width: 800px) {
  .column_2 {
    -ms-flex: 50%;
    flex: 50%;
    max-width: 50%;
  }
}

/* Responsive layout - makes the two columns stack on top of each other instead of next to each other */
@media screen and (max-width: 600px) {
  .column_2 {
    -ms-flex: 100%;
    flex: 100%;
    max-width: 100%;
  }
}

th {
  text-align: right;
}


table { border-collapse: separate; border-spacing: 5px; } /* cellspacing="5" */

table.center {
    margin-left:-15px;
  }

#map-canvas { height: 100% }

.call {
text-align: center;
}

.hours {
text-align: center;
}

</style>
<template>
<body>

<!-- Header -->
<div class="header">
  <h1>Tejratna Eye and Ear Care Centre</h1>
</div>

<div class="row_2">
  <div class="column_2">
    <div class="call">
      <p><i class="fa fa-calendar" style="font-size:20px;color:green"></i> MAKE AN APPOINTMENT</p>
      <p><i class="fa fa-phone" style="font-size:20px;color:green"></i> +977-985-2060177</p>
    </div>
    <div class="hours">
    <p><i class="fa fa-clock-o" style="font-size:20px;color:green"></i> Hours</p>
    </div>
    <table class="center">
    <tr><th>Sunday:</th><td>9am - 5pm</td></tr>
    <tr><th>Monday:</th><td>9am - 5pm</td></tr>
    <tr><th>Tuesday:</th><td>9am - 5pm</td></tr>
    <tr><th>Wednesday:</th><td>9am - 5pm</td></tr>
    <tr><th>Thursday:</th><td>9am - 5pm</td></tr>
    <tr><th>Friday:</th><td>9am - 5pm</td></tr>
    <tr><th>Saturday:</th><td>Closed</td></tr>
    </table>
  </div>

  <div class="column_2">
  <div id="map-canvas"></div>
<script src="http://maps.google.com/maps/api/js?sensor=false"></script>
<script>
  function getLocation() {
      if (navigator.geolocation) {
          navigator.geolocation.getCurrentPosition(initialize, showError);
      }
      else {
          alert("Geolocation is not supported by this browser.");
      }
  }

  function initialize(position) {
      // If you don't use 'var' before a variable, it will be accessible globally,
      // which makes it easier (bad) to overwrite/clobber if you reuse these names elsewhere
      var lat = position.coords.latitude,
          lon = position.coords.longitude;

      var mapOptions = {
          center: new google.maps.LatLng(lat, lon),
          zoom: 14,
          mapTypeId: google.maps.MapTypeId.ROADMAP,
          mapTypeControl: true
      }

      var map = new google.maps.Map(document.getElementById("map-canvas"), mapOptions);
      var marker = new google.maps.Marker({
          position: new google.maps.LatLng(lat, lon),
          map: map,
          title: "Current Location"
      });
  }

  function showError(error) {
      switch (error.code) {
          case error.PERMISSION_DENIED:
              alert("User denied the request for Geolocation.");
              break;
          case error.POSITION_UNAVAILABLE:
              alert("Location information is unavailable.");
              break;
          case error.TIMEOUT:
              alert("The request to get user location timed out.");
              break;
          case error.UNKNOWN_ERROR:
              alert("An unkown error occurred.");
              break;
      }
  }

  // When the page has loaded, call the getLocation function
  // Be sure not to use parenthesis after getLocation, or you will
  // call it, instead of passing a reference to it to be called later (callback)
  google.maps.event.addDomListener(window, 'load', getLocation);
</script>
  </div>
</div>


<!-- Photo Grid -->
<div class="row">
  <div class="column">
    <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_1.jpg" style="width:100%">
      <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_2.jpg" style="width:100%">
        <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_3.jpg" style="width:100%">
          <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_4.jpg" style="width:100%">
          <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_20.jpg" style="width:100%">

  </div>
  <div class="column">
  <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_5.jpg" style="width:100%">
    <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_6.jpg" style="width:100%">
      <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_7.jpg" style="width:100%">
        <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_8.jpg" style="width:100%">
        <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_19.jpg" style="width:100%">
  </div>
  <div class="column">
  <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_9.jpg" style="width:100%">
    <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_10.jpg" style="width:100%">
      <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_11.jpg" style="width:100%">
        <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_12.jpg" style="width:100%">
        <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_18.jpg" style="width:100%">
  </div>
  <div class="column">
  <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_13.jpg" style="width:100%">
    <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_14.jpg" style="width:100%">
      <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_15.jpg" style="width:100%">
        <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_16.jpg" style="width:100%">
        <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_17.jpg" style="width:100%">
  </div>
</div>
</body>
</template>
