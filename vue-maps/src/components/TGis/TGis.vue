<template>
  <div class="t-gis-container">
    <t-gis-map
      :center="centerCoords"
      :markers="comboCoords"
      :styles="{width: '950px', height: '600px'}"
      :zoom="8"
    ></t-gis-map>
  </div>
</template>

<script>
import tGisMap from '../tGisMap';

export default {
  name: 'TGis',
  components: { tGisMap },
  data: () => ({
    centerCoords: [44.95806, 34.11], // Simf
    coords1: [44.9, 34],
    coords2: [45, 34],
    coords3: [44.9, 34.1],
    comboCoords: [[44.9, 34], [45, 34], [44.9, 34.1]]
  }),
}
</script>

<style>
.t-gis-container {
  margin: 0 auto;
  height: 600px;
  width: 950px;
}
</style>
