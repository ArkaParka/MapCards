<template>
  <div id="app">
    <YMap />
    <br>
    <TGis />
  </div>
</template>

<script>
// https://vue-yandex-maps.github.io/guide/Map.html#attributes
// https://yandex.ru/dev/maps/jsapi/doc/2.1/dg/concepts/geoobjects.html

import YMap from "./components/YMap/YMap";
import TGis from "./components/TGis/TGis";

export default {
  name: 'app',
  components: { TGis, YMap },
  data: () => ({
    centerCoords: [44.95806, 34.11], // Simf
    coords1: [44.9, 34],
    coords2: [45, 34],
    coords3: [44.9, 34.1],
    comboCoords: [[44.9, 34], [45, 34], [44.9, 34.1]]
  })
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
