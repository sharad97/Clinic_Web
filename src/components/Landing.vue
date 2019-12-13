<style>

.google-maps {
    position: relative;
    padding-bottom: 75%; // This is the aspect ratio
    height: 0;
    overflow: hidden;
}
.google-maps iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 100% !important;
    height: 50% !important;
}

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

th {
  text-align: right;
}

table { border-collapse: separate; border-spacing: 5px; } /* cellspacing="5" */


.phone {
  position: relative;
}

.hours {
  position: relative;
}

</style>

<template>
<body>

<!-- Header -->
<div class="header">
  <h1>Tejratna Eye and Ear Care Centre</h1>
</div>
<div>
  <div class="phone">
  <p>MAKE AN APPOINTMENT</p>
  <p class="fa fa-phone">+977-985-2060177</p>
  </div>
  <div class="hours">
    <table>
      <tr><th>Hours</th><td></td></tr>
      <tr><th>Sunday:</th><td>9am - 5pm</td></tr>
      <tr><th>Monday:</th><td>9am - 5pm</td></tr>
      <tr><th>Tuesday:</th><td>9am - 5pm</td></tr>
      <tr><th>Wednesday:</th><td>9am - 5pm</td></tr>
      <tr><th>Thursday:</th><td>9am - 5pm</td></tr>
      <tr><th>Friday:</th><td>9am - 5pm</td></tr>
      <tr><th>Saturday:</th><td>Closed</td></tr>
      </table>
  </div>
  <div class="google-maps">
    <iframe width="400" height="400" frameborder="0" style="border:0" src="https://www.google.com/maps/embed/v1/place?q=place_id:ChIJzSfxBx7H6DkR5PJeX2cmXPA&key=AIzaSyBKtVdM9lqOznPQqEs82kQJanJEga1NhTg" allowfullscreen></iframe>
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
