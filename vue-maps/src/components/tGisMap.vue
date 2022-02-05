<template>
  <div>
    <div id="2GisMap" :style="styles"></div>
  </div>
</template>

<script>
import gMap from '2gis-maps'
import { Clusterer } from '@2gis/mapgl-clusterer';

export default {
  name: 'tGisMap',
data: () => ({
  centerCoords: [44.95806, 34.11], // Simf
  coords1: [44.9, 34],
  coords2: [45, 34],
  coords3: [44.9, 34.1],
  comboCoords: [[44.9, 34], [45, 34], [44.9, 34.1]]
}),
  props: {
    center: {
      type: Array,
      default: []
    },
    markers: {
      type: Array,
      default: []
    },
    zoom: {
      type: Number,
      default: 13
    },
    styles: {
      type: Object,
      default: () => {
        return {width: '500px', height: '400px'}
      }
    }
  },
  methods: {
    init() {
      let map
      gMap.then(() => {
        map = new DG.map('2GisMap', {
          'center': this.center,
          'zoom': this.zoom
        });
        DG.polygon(this.markers).addTo(map)

        // this.markers.forEach(coords => {
        //   console.log('coords', coords);
        //   DG.marker(coords).addTo(map)
        // });

        // const clusterer = new Clusterer(map, {
        //   radius: 60,
        // });
        // const m = [
        //   { coordinates: [55.27887, 25.21001] },
        //   { coordinates: [55.30771, 25.20314] },
        //   { coordinates: [55.35266, 25.24382] },
        // ];
        // clusterer.load(m);
      })
    }
  },
  created() {
    this.init()
  }
}
</script>
