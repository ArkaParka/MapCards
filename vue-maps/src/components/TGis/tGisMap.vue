<template>
  <div>
    <div id="tGisMap" :style="styles"></div>
  </div>
</template>

<script>
import DG from '2gis-maps';

export default {
  name: 'tGisMap',
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
      let markers = this.markers;
      let center = this.center;
      let zoom = this.zoom;
      let map = null;

      DG.then(function() {
        // загрузка кода модуля
        return DG.plugin('https://unpkg.com/leaflet.markercluster@1.4.1/dist/leaflet.markercluster.js');
      }).then(function() {
        map = DG.map('tGisMap', {
          center: center,
          zoom: zoom
        });

        let markerClusterGroup = DG.markerClusterGroup();

        // обработка координат для установки маркеров
        for (let i = 0; i < markers.length; i++) {
          let title = 'hello';
          let marker = DG.marker(markers[i], { title: title });
          marker.bindPopup(title);
          markerClusterGroup.addLayer(marker);
        }

        map.addLayer(markerClusterGroup);
      });
    }
  },
  created() {
    this.init()
  }
}
</script>
