<script>
export default {
  data() {
    return {
      map: "",
      popup: "",
      Popup: ""
    };
  },
  methods: {
    definePopupClass() {
      /**
       * A customized popup on the map.
       * @param {!google.maps.LatLng} position
       * @param {!Element} content
       * @constructor
       * @extends {google.maps.OverlayView}
       */
      this.Popup = function(position, content) {
        this.position = position;

        content.classList.add("popup-bubble-content");

        var pixelOffset = document.createElement("div");
        pixelOffset.classList.add("popup-bubble-anchor");
        pixelOffset.appendChild(content);

        this.anchor = document.createElement("div");
        this.anchor.classList.add("popup-tip-anchor");
        this.anchor.appendChild(pixelOffset);

        // Optionally stop clicks, etc., from bubbling up to the map.
        this.stopEventPropagation();
      };
      // NOTE: google.maps.OverlayView is only defined once the Maps API has
      // loaded. That is why Popup is defined inside initMap().
      this.Popup.prototype = Object.create(google.maps.OverlayView.prototype);

      /** Called when the popup is added to the map. */
      this.Popup.prototype.onAdd = function() {
        this.getPanes().floatPane.appendChild(this.anchor);
      };

      /** Called when the popup is removed from the map. */
      this.Popup.prototype.onRemove = function() {
        if (this.anchor.parentElement) {
          this.anchor.parentElement.removeChild(this.anchor);
        }
      };

      /** Called when the popup needs to draw itself. */
      this.Popup.prototype.draw = function() {
        var divPosition = this.getProjection().fromLatLngToDivPixel(
          this.position
        );
        // Hide the popup when it is far out of view.
        var display =
          Math.abs(divPosition.x) < 4000 && Math.abs(divPosition.y) < 4000
            ? "block"
            : "none";

        if (display === "block") {
          this.anchor.style.left = divPosition.x + "px";
          this.anchor.style.top = divPosition.y + "px";
        }
        if (this.anchor.style.display !== display) {
          this.anchor.style.display = display;
        }
      };

      /** Stops clicks/drags from bubbling up to the map. */
      this.Popup.prototype.stopEventPropagation = function() {
        var anchor = this.anchor;
        anchor.style.cursor = "auto";

        [
          "click",
          "dblclick",
          "contextmenu",
          "wheel",
          "mousedown",
          "touchstart",
          "pointerdown"
        ].forEach(function(event) {
          anchor.addEventListener(event, function(e) {
            e.stopPropagation();
          });
        });
      };
    }
  },
  mounted() {
    this.$nextTick(() => {
      this.definePopupClass();
      this.map = new google.maps.Map(document.getElementById("map"), {
        center: { lat: 27.378349, lng: 87.206579 },
        zoom: 19
      });

      this.popup = new this.Popup(
        new google.maps.LatLng(27.378349, 87.206579),
        document.getElementById("content")
      );
      this.popup.setMap(this.map);
    });
  }
};
</script>

<style>
#map {
height:300px;
width: 100%;
}

body {
  margin: 0;
  padding-right:50px;
  padding-left: 50px;
  font-family: Arial;
}

@media screen and (max-width: 800px) {
body {
  margin: 0;
  padding-right:25px;
  padding-left: 25px;
  font-family: Arial;
}
}
@media screen and (max-width: 600px) {
body {
  margin: 0;
  padding-right:0px;
  padding-left: 0px;
  font-family: Arial;
}
}

/* The location pointed to by the popup tip. */
.popup-tip-anchor {
  height: 0;
  position: absolute;
  /* The max width of the info window. */
  width: 200px;
}
/* The bubble is anchored above the tip. */
.popup-bubble-anchor {
  position: absolute;
  width: 100%;
  bottom: /* TIP_HEIGHT= */ 8px;
  left: 0;
}
/* Draw the tip. */
.popup-bubble-anchor::after {
  content: "";
  position: absolute;
  top: -1px;
  left: 0;
  /* Center the tip horizontally. */
  transform: translate(-50%, 0);
  /* The tip is a https://css-tricks.com/snippets/css/css-triangle/ */
  width: 0;
  height: 0;
  /* The tip is 8px high, and 12px wide. */
  border-left: 6px solid transparent;
  border-right: 6px solid transparent;
  border-top: /* TIP_HEIGHT= */ 8px solid white;
}
/* The popup bubble itself. */
.popup-bubble-content {
  position: absolute;
  top: 0;
  left: 0;
  transform: translate(-50%, -100%);
  /* Style the info window. */
  background-color: white;
  padding: 5px;
  border-radius: 3px;
  font-family: sans-serif;
  overflow-y: auto;
  max-height: 60px;
  box-shadow: 0px 2px 10px 1px rgba(0, 0, 0, 0.5);
}



* {
  box-sizing: border-box;
}

.header {
  text-align: center;
  padding: 32px;
}

.row_1 {
  display: -ms-flexbox; /* IE10 */
  display: flex;
  -ms-flex-wrap: wrap; /* IE10 */
  flex-wrap: wrap;
  padding: 0 4px;
}

/* Create four equal columns that sits next to each other */
.column_1 {
  -ms-flex: 33%; /* IE10 */
  flex: 33%;
  max-width: 33%;
  padding: 0 4px;
}

.column_1 img {
  margin-top: 8px;
  vertical-align: middle;
  width: 100%;
}

/* Responsive layout - makes a two column-layout instead of four columns */
@media screen and (max-width: 800px) {
  .column_1 {
    -ms-flex: 50%;
    flex: 50%;
    max-width: 50%;
  }
}

/* Responsive layout - makes the two columns stack on top of each other instead of next to each other */
@media screen and (max-width: 600px) {
  .column_1 {
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

.row_3 {
  display: -ms-flexbox; /* IE10 */
  display: flex;
  -ms-flex-wrap: wrap; /* IE10 */
  flex-wrap: wrap;
  padding: 0 4px;
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

#myCarousel{
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 100%;
}

.contacts{
padding-top: 10px;
}

.slides{
display: block;
margin-left: auto;
margin-right: auto;
height:auto;
max-height: 500px;
width: 100%;
}

</style>



<template>
<body>

<!-- Header -->
<div class="header">
  <h1>Tejratna Eye and Ear Care Centre</h1>
</div>


<div class="row_3">
  <div id="myCarousel" class="carousel slide" data-ride="carousel">
    <!-- Indicators -->
    <ol class="carousel-indicators">
      <li data-target="#myCarousel" data-slide-to="0" class="active"></li>
      <li data-target="#myCarousel" data-slide-to="1"></li>
    </ol>

    <!-- Wrapper for slides -->
    <div class="carousel-inner">
      <div class="item active">
        <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/slide_1.jpg" alt="slide_1" class="slides">
      </div>

      <div class="item">
        <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/slide_2.jpg" alt="slide_2" class="slides">
      </div>
    </div>

    <!-- Left and right controls -->
    <a class="left carousel-control" href="#myCarousel" data-slide="prev">
      <span class="glyphicon glyphicon-chevron-left"></span>
      <span class="sr-only">Previous</span>
    </a>
    <a class="right carousel-control" href="#myCarousel" data-slide="next">
      <span class="glyphicon glyphicon-chevron-right"></span>
      <span class="sr-only">Next</span>
    </a>
  </div>
</div>

<div class="row_2">
  <div class="column_2">
  <div class="contacts">
    <div class="call">
      <p><i class="fa fa-calendar" style="font-size:20px;color:green"></i> MAKE AN APPOINTMENT</p>
      <p>Schedule your visit by dialing our office</p>
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
  </div>

  <div class="column_2">
    <div id="map"></div>
    <div id="content">
      Tejratna Eye and Ear Care Centre
    </div>
   </div>
</div>


<!-- Photo Grid -->
<div class="row_1">
  <div class="column_1">
    <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_1.jpg" style="width:100%">
      <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_2.jpg" style="width:100%">
        <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_3.jpg" style="width:100%">
          <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_20.jpg" style="width:100%">
          <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_5.jpg" style="width:100%">
            <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_6.jpg" style="width:100%">
  </div>
  <div class="column_1">
  <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_9.jpg" style="width:100%">
    <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_10.jpg" style="width:100%">
      <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_11.jpg" style="width:100%">
        <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_12.jpg" style="width:100%">
        <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_7.jpg" style="width:100%">
            <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_8.jpg" style="width:100%">
  </div>
  <div class="column_1">
  <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_13.jpg" style="width:100%">
    <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_14.jpg" style="width:100%">
      <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_15.jpg" style="width:100%">
        <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_16.jpg" style="width:100%">
        <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_17.jpg" style="width:100%">
        <img src="https://12webimage.s3-us-west-1.amazonaws.com/clinic_web/clinic_19.jpg" style="width:100%">

  </div>
</div>
</body>
</template>
