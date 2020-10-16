<template>
  <div id="container">
    <div id="mapContainer"></div>
  </div>
</template>

<script>
import L from "leaflet";
import "leaflet/dist/leaflet.css";
import { mapBoxKey } from "../../.keys";
import { onMounted, watchEffect } from "vue";
export default {
  props: {
    loc: Object,
  },
  setup(props) {
    let myMap;
    onMounted(() => {
      myMap = L.map("mapContainer").setView([51.505, -0.09], 13);

      L.tileLayer(
        "https://api.mapbox.com/styles/v1/{id}/tiles/{z}/{x}/{y}?access_token={accessToken}",
        {
          attribution:
            'Map data &copy; <a href="https://www.openstreetmap.org/">OpenStreetMap</a> contributors, <a href="https://creativecommons.org/licenses/by-sa/2.0/">CC-BY-SA</a>, Imagery © <a href="https://www.mapbox.com/">Mapbox</a>',
          maxZoom: 18,
          id: "mapbox/streets-v11",
          tileSize: 512,
          zoomOffset: -1,
          accessToken: mapBoxKey,
        }
      ).addTo(myMap);
    });

    watchEffect(() => {
      console.log("loc", props.loc);
      if (myMap && props.loc) myMap.setView([props.loc.lat, props.loc.lng]);
    });
  },
};
</script>

<style scoped>
#mapContainer {
  width: 100%;
  height: 400px;
}
</style>