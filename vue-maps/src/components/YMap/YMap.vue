<template>
  <div class="ymap-container">
    <yandex-map
      :coords="centerCoords"
      :zoom="zoom"
      :cluster-options="clusterOptions"
      @click="onClick">
      <ymap-marker
        marker-id="1"
        marker-type="Placemark"
        :coords="centerCoords"
        cluster-name="1"
        :balloon="{header: 'My coords ' + centerCoords}"
        :balloon-template="balloonTemplate"
      ></ymap-marker>
      <ymap-marker
        marker-id="2"
        marker-type="Placemark"
        :coords="coords1"
        cluster-name="1"
        :balloon="{header: 'My coords ' + coords1}"
        :balloon-template="balloonTemplate"
      ></ymap-marker>
      <ymap-marker
        marker-id="3"
        marker-type="Placemark"
        :coords="coords2"
        cluster-name="1"
        :balloon="{header: 'My coords ' + coords2}"
        :balloon-template="balloonTemplate"
      ></ymap-marker>
      <ymap-marker
        marker-id="4"
        marker-type="Placemark"
        :coords="coords3"
        cluster-name="1"
        :balloon="{header: 'My coords ' + coords3}"
        :balloon-template="balloonTemplate"
      ></ymap-marker>
    </yandex-map>
  </div>
</template>

<script>
// Дока https://vue-yandex-maps.github.io/examples/

import {yandexMap, ymapMarker} from "vue-yandex-maps";

export default {
  name: 'YMap',
  components: { yandexMap, ymapMarker },
  data: () => ({
    zoom: 8,
    clusterOptions: {
      1: {
        clusterDisableClickZoom: true,
        clusterOpenBalloonOnClick: true,
        clusterBalloonLayout: [
          '<ul class=list>',
          '{% for geoObject in properties.geoObjects %}',
          '<li><a href=# class="list_item">{{ geoObject.properties.balloonContentHeader|raw }}</a></li>',
          '{% endfor %}',
          '</ul>',
        ].join(''),
      },
    },
    centerCoords: [44.95806, 34.11], // Simf
    coords1: [44.9, 34],
    coords2: [45, 34],
    coords3: [44.9, 34.1],
    comboCoords: [[44.9, 34], [45, 34], [44.9, 34.1]]
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
      // Добавление координатных точек при клике по карте
      this.centerCoords = e.get('coords');
    }
  }
}
</script>

<style>
.ymap-container {
  margin: 0 auto;
  height: 600px;
  width: 950px;
}
</style>
