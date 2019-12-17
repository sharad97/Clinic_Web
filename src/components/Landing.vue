<script>
import gmapsInit from '../utils/gmaps';
const locations = [
  {
    position: {
      lat: 48.160910,
      lng: 16.383330,
    },
  },
  {
    position: {
      lat: 48.174270,
      lng: 16.329620,
    },
  },
  {
    position: {
      lat: 48.146140,
      lng: 16.297030,
    },
  },
  {
    position: {
      lat: 48.135830,
      lng: 16.194460,
    },
  },
  {
    position: {
      lat: 48.306091,
      lng: 14.286440,
    },
  },
  {
    position: {
      lat: 47.503040,
      lng: 9.747070,
    },
  },
];
export default {
  name: `App`,
  async mounted() {
    try {
      const google = await gmapsInit();
      const geocoder = new google.maps.Geocoder();
      const map = new google.maps.Map(this.$el);
      geocoder.geocode({ address: `Austria` }, (results, status) => {
        if (status !== `OK` || !results[0]) {
          throw new Error(status);
        }
        map.setCenter(results[0].geometry.location);
        map.fitBounds(results[0].geometry.viewport);
      });
      const markerClickHandler = (marker) => {
        map.setZoom(13);
        map.setCenter(marker.getPosition());
      };
      const markers = locations
        .map((location) => {
          const marker = new google.maps.Marker({ ...location, map });
          marker.addListener(`click`, () => markerClickHandler(marker));
          return marker;
        });

    } catch (error) {
      // eslint-disable-next-line no-console
      console.error(error);
    }
  },
};
</script>


<style>

.App {
  width: 100vw;
  height: 100vh;
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
  <div class="google-map" :id="mapName"></div>
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
