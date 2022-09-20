<template>
  <div class="flex flex-col h-screen max-h-screen">
    <div class=" z-20 flex justify-center relative bg-hero-pattern bg-cover px-4 pt-8 pb-32">
      <div class="w-full max-w-screen-sm">
        <h1 class="text-white text-center text-3xl pb-4">IP Address Tracker</h1>
        <div class="flex">
          <input class="flex-1 py-3 px-2 rounded-tl-md rounded-bl-md focus:outline-none" type="text"
            placeholder="Search for an IP address or leave empty to get your ip info">
          <i
            class="fa-solid fa-chevron-right cursor-pointer bg-black text-white px-4 rounded-tr-md rounded-br-md flex items-center"></i>
        </div>
      </div>
      <IPInfo />
    </div>
    <div id="map" class="h-full z-10">{{mymap}}</div>
  </div>
</template>

<script>
// @ is an alias to /src
import IPInfo from '@/components/IPInfo.vue'
import leaflet from 'leaflet'
import { onMounted } from 'vue'
export default {
  name: 'HomeView',
  components: {
    IPInfo,
  },
  setup() {
    let mymap;
    onMounted(() => {
      mymap = leaflet.map('map').setView([51.505, -0.09], 13);
      leaflet.tileLayer('https://api.mapbox.com/styles/v1/mapbox/streets-v11/tiles/{z}/{x}/{y}?access_token=pk.eyJ1Ijoia255c25hY29kZXIiLCJhIjoiY2w4OXhnNWxzMDAzZDNwcXFhb2NudTdiciJ9.rE5gYw_igcoMHcs82sA0tg',
        {
          attribution: '© <a href="https://www.mapbox.com/feedback/">Mapbox</a> © <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>',
          tileSize: 512,
          zoomOffset: -1
        }).addTo(mymap);
    })

  },
}
</script>
