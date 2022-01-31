<template>
  <div id="app">
    <div class="ymap-container">
      <yandex-map
        :coords="centerCoords"
        :zoom="8"
        @click="onClick">
        <ymap-marker
          marker-id="1"
          marker-type="Placemark"
          :coords="centerCoords"
          :balloon-template="balloonTemplate"
        ></ymap-marker>
        <ymap-marker
          marker-id="2"
          marker-type="Placemark"
          :coords="coords1"
          :balloon-template="balloonTemplate"
        ></ymap-marker>
        <ymap-marker
          marker-id="3"
          marker-type="Placemark"
          :coords="coords2"
          :balloon-template="balloonTemplate"
        ></ymap-marker>
        <ymap-marker
          marker-id="4"
          marker-type="Placemark"
          :coords="coords3"
          :balloon-template="balloonTemplate"
        ></ymap-marker>
      </yandex-map>
    </div>
    <div class="t-gis">
      <t-gis-map
        :center="[54.98, 82.89]"
        :marker="[54.98, 82.89]"
        :styles="{width: '300px', height: '200px'}"
        :zoom="16"
      ></t-gis-map>
    </div>
  </div>
</template>

<script>
// https://vue-yandex-maps.github.io/guide/Map.html#attributes
// https://yandex.ru/dev/maps/jsapi/doc/2.1/dg/concepts/geoobjects.html

import {yandexMap, ymapMarker} from "vue-yandex-maps";
import tGisMap from './components/tGisMap'

export default {
  name: 'app',
  components: { yandexMap, ymapMarker, tGisMap },
  data: () => ({
    centerCoords: [44.95806, 34.11], // Simf
    coords1: [44.9, 34],
    coords2: [45, 34],
    coords3: [44.9, 34.1],
  }),
  computed: {
    balloonTemplate() {
      return `
        <h1 class="red">Hi, everyone!</h1>
        <p>I am here: ${this.centerCoords}</p>
        <img src="http://via.placeholder.com/350x150">
      `
    }
  },
  methods: {
    onClick(e) {
      this.centerCoords = e.get('coords');
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.ymap-container {
  margin: 0 auto;
  height: 600px;
  width: 950px;
}
.red {
  color: red;
}
</style>
