<template>
  <div class="weather-container"  :style="{ backgroundImage: `url(${require('@/assets/conditions/' + backgroundImage)})` }">
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
      weather: {} as WeatherType,
      backgroundImage:"background.png"
    };
  },
  methods: {
    getWeather(weather: WeatherType) {
      this.weather = weather 
      this.generateBackgroundImage(weather.weather[0].icon)
    },
    generateBackgroundImage(icon:string) {
      switch (icon) {
        case '03n':
          this.backgroundImage = 'clouds.jpeg'
          break;
        case '11d':
          this.backgroundImage = 'thunderstorm.jpeg'
          break;
        case '09d':
          this.backgroundImage = 'drizzle.jpeg'
          break;
        case '13d':
          this.backgroundImage = 'snow.jpeg'
          break;
        case '01d':
          this.backgroundImage = 'clear.jpeg'
          break;
        case '02d':
          this.backgroundImage = 'clouds.jpeg'
          break;
        default:
          break;
      }
    }
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