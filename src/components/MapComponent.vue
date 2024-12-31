<template>
  <div v-if="markerLatLng" class="map-component">
    <l-map :zoom="zoom" :center="markerLatLng" style="height: 70vh; width: 100%">
      <l-tile-layer :url="url" :attribution="attribution" />
      <l-marker :lat-lng="markerLatLng" />
    </l-map>
  </div>
</template>

<script>
import { LMap, LMarker, LTileLayer } from '@vue-leaflet/vue-leaflet'

export default {
  name: 'MapComponent',
  components: {
    LMap,
    LTileLayer,
    LMarker,
  },
  props: {
    markerLatLng: {
      type: Array,
      required: true,
      default: () => [0, 0],
    },
    zoom: {
      type: Number,
      default: 6,
    },
  },
  data() {
    return {
      url: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
      attribution:
        '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors',
    }
  },
  mounted() {
    console.log('heyeyy', this.markerLatLng)
  },
}
</script>

<style></style>
