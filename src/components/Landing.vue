

<script>
export default {
  name: 'hello',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }},
    methods: {
    function(){
  var popup, Popup;

        console.log("map: ", google.maps)
        var lat = 27.37834;
        var lng = 87.206579;
        var map = new google.maps.Map(document.getElementById('myMap'), {
            center: {lat:lat, lng:lng};
            scrollwheel: false,
            zoom: 20
            });

        Popup = createPopupClass();

popup = new Popup(
    new google.maps.LatLng(lat, lng),
    document.getElementById('content'));
popup.setMap(map);
},

function createPopupClass() {

function Popup(position, content) {
  this.position = position;

  content.classList.add('popup-bubble');

  // This zero-height div is positioned at the bottom of the bubble.
  var bubbleAnchor = document.createElement('div');
  bubbleAnchor.classList.add('popup-bubble-anchor');
  bubbleAnchor.appendChild(content);

  // This zero-height div is positioned at the bottom of the tip.
  this.containerDiv = document.createElement('div');
  this.containerDiv.classList.add('popup-container');
  this.containerDiv.appendChild(bubbleAnchor);

  // Optionally stop clicks, etc., from bubbling up to the map.
  google.maps.OverlayView.preventMapHitsAndGesturesFrom(this.containerDiv);
},
// ES5 magic to extend google.maps.OverlayView.
Popup.prototype = Object.create(google.maps.OverlayView.prototype);

/** Called when the popup is added to the map. */
Popup.prototype.onAdd = function() {
  this.getPanes().floatPane.appendChild(this.containerDiv);
},

/** Called when the popup is removed from the map. */
Popup.prototype.onRemove = function() {
  if (this.containerDiv.parentElement) {
    this.containerDiv.parentElement.removeChild(this.containerDiv);
  }
},

/** Called each frame when the popup needs to draw itself. */
Popup.prototype.draw = function() {
  var divPosition = this.getProjection().fromLatLngToDivPixel(this.position);

  // Hide the popup when it is far out of view.
  var display =
      Math.abs(divPosition.x) < 4000 && Math.abs(divPosition.y) < 4000 ?
      'block' :
      'none';

  if (display === 'block') {
    this.containerDiv.style.left = divPosition.x + 'px';
    this.containerDiv.style.top = divPosition.y + 'px';
  }
  if (this.containerDiv.style.display !== display) {
    this.containerDiv.style.display = display;
  }
}

return Popup;


}
  },
  mounted() {
   this.function();

}
}
</script>
<style scoped>
    #myMap {
    height:300px;
    width: 100%;
   }
</style>

<style>

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
  <div id="myMap"></div>
  <div id="content">
  Hello world!
</div>
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
