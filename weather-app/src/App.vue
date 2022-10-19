<template>
  <div id="app">
    <weatherApp />
  </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue';
import weatherApp from './components/weather-app.vue'
export default defineComponent({
  name: 'App',
  components: {
    weatherApp
  }
});
</script>
<style>

</style>