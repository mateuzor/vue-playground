<template>
     <div class="weather-info" v-if="weather.main">
        <div class="location-box">
          <div class="location">
            {{weather?.name}},{{weather.sys?.country }}
          </div>
          <div class="date">{{ todaysDate() }}</div>
        </div>
        <div class="weather-box">
          <div class="temp">{{ Math.round(weather.main?.temp) }}°c</div>
          <div class="weather">{{ weather.weather?.[0].main }}</div>
        </div>
      </div>
</template>
<script lang="ts">
import WeatherType from '@/types/Weather';
import {defineComponent,PropType} from 'vue'
export default defineComponent({
  name: 'WeatherDetails',
  props: {
    weather: {
      type: Object as PropType<WeatherType>,
      required: true
    },
  },
  methods: {
    todaysDate() {
            const months = [
                "Jan",
                "Feb",
                "Mar",
                "Apr",
                "May",
                "Jun",
                "Jul",
                "Aug",
                "Sep",
                "Oct",
                "Nov",
                "Dec",
            ];
            const days = ["Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"];
            let d = new Date();
            let month = months[d.getMonth()];
            let day = days[d.getDay()];
            let date = d.getDate();
            let year = d.getFullYear();
            return `${month} ${date} ${day} ${year}`;
        }
  }
})
</script>
<style>
@import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@300;500;700;900&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Montserrat";
}

.location-box .location {
  color: #fff;
  font-size: 32px;
  font-weight: 500;
  font-style: italic;
  text-align: center;
  margin-top: 30px;
}

.location-box .date {
  color: #fff;
  font-size: 20px;
  font-weight: 300;
  text-align: center;
}

.weather-box {
  text-align: center;
}

.weather-box .temp {
  display: inline-block;
  padding: 10px 25px;
  color: #fff;
  font-size: 102px;
  font-weight: 900;
  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.25);
  border-radius: 16px;
  margin: 30px 0px;
  box-shadow: 3px 6px rgba(0, 0, 0, 0.25);
  font-style: italic;
}

.weather-box .weather {
  color: #fff;
  font-size: 48px;
  font-weight: 700;
  font-style: italic;
  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}
</style>