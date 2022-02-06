<template>
  <div id="app">
    <YMap :coords="coords" />
    <br>
    <TGis :coords="coords" />
  </div>
</template>

<script>
// YMap https://vue-yandex-maps.github.io/guide/Map.html#attributes
// 2Gis https://yandex.ru/dev/maps/jsapi/doc/2.1/dg/concepts/geoobjects.html
// -------------------
// gMap https://www.npmjs.com/package/gmap-vue
// gMap https://diegoazh.github.io/gmap-vue/#get-an-api-key-from-google

import YMap from "./components/YMap/YMap";
import TGis from "./components/TGis/TGis";

export default {
  name: 'app',
  components: { TGis, YMap },
  data: () => (
    {
      coords: {
        center: [44.95806, 34.11], // Simf
        one: [44.9, 34],
        two: [45, 34],
        three: [44.9, 34.1],
        arr: [[44.9, 34], [45, 34], [44.9, 34.1], [44.95806, 34.11]]
      }
  }
  )
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
</style>
