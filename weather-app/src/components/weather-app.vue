<template>
  <div class="weather-container">
    <div class="weather-wrap">
      <SearchComponent @weather="getWeather" />
      <WeatherDetails :weather="weather" />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import WeatherType from '../types/Weather'
import WeatherDetails from "./weather-details.vue";
import SearchComponent from './search-component.vue'
export default defineComponent({
  components: { WeatherDetails, SearchComponent },
  data() {
    return {
      weather: {} as WeatherType
    };
  },
  methods: {
    getWeather(weather: WeatherType) {
      this.weather = weather 
    },
  },
});
</script>
<style>
@import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@300;500;700;900&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Montserrat";
}

.weather-container {
  background-image: url("../assets/background.png");
  background-size: cover;
  background-position: center;
  transition: 0.4s;
  width: 375px;
  margin: 0 auto;
  border-radius: 25px;
  margin-top: 50px;
  box-shadow: 0px 0px 30px #00000065;
}

.weather-wrap {
  height: 600px;
  padding: 25px;
  border-radius: 25px;
  background-image: linear-gradient(to bottom,
      rgba(0, 0, 0, 0.15),
      rgba(0, 0, 0, 0.4));
}
</style>