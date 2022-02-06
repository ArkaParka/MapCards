<template>
  <div class="ymap-container">
    <yandex-map
      :coords="coords.center"
      :zoom="zoom"
      :cluster-options="clusterOptions"
      @click="onClick">
      <ymap-marker v-for="coords in coords.arr" :key="coords.toString()"
        :marker-id="coords.toString()"
        marker-type="Placemark"
        :coords="coords"
        cluster-name="firstCluster"
        :balloon="{header: 'My coords ' + coords}"
        :balloon-template="balloonTemplate"
      ></ymap-marker>
    </yandex-map>
  </div>
</template>

<script>
// Дока https://vue-yandex-maps.github.io/examples/
// Дока https://yandex.ru/dev/maps/jsapi/doc/2.1/ref/reference/Balloon.html

import {yandexMap, ymapMarker} from "vue-yandex-maps";

export default {
  name: 'YMap',
  components: { yandexMap, ymapMarker },
  props: {
    coords: {}
  },
  data: () => ({
    zoom: 8,
    clusterOptions: {
      firstCluster: {
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
  }),
  computed: {
    balloonTemplate() {
      return `
        <h1 class="red">Hi, everyone!</h1>
        <p>I am here: ${this.coords.center}</p>
        <img src="http://via.placeholder.com/350x150">
      `
    }
  },
  methods: {
    onClick(e) {
      // Перенос точки при клике по карте
      this.coords.center = e.get('coords');
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
