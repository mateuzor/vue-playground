<template>
    <div class="search-box">
        <input type="text" placeholder="Search..." class="search-bar" v-model="query" v-on:keypress="fetchWeather" />
    </div>
</template>

<script lang="ts">
import axios from "axios";
import { defineComponent } from 'vue'
import WeatherType from '../types/Weather'
export default defineComponent({
    name: 'SearchComponent',
    data() {
        return {
            api_key: "28953c7f3c1d3e66c812efd326e55f9d",
            url_base: "https://api.openweathermap.org/data/2.5/",
            weather_icon: "http://openweathermap.org/img/wn/",
            query: "",
            weather: {} as WeatherType
        };
    },
    methods: {
        async fetchWeather(e: KeyboardEvent) {
            if (e.key == "Enter") {
                let response = await axios.get(`${this.url_base}weather?q=${this.query}&units=metric&APPID=${this.api_key}`);
                this.setResults(response.data);
            }
        },
        setResults(returnedResponse: WeatherType) {
            this.weather = returnedResponse;
            this.$emit('weather', this.weather);
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

.search-box .search-bar {
    display: block;
    width: 100%;
    padding: 15px;
    color: #313131;
    font-size: 20px;
    appearance: none;
    border: none;
    outline: none;
    background: none;
    background-color: rgba(255, 255, 255, 0.5);
    box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.25);
    border-radius: 10px;
    transition: 0.4s;
}

.search-box .search-bar:focus {
    box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);
    background-color: rgba(255, 255, 255, 0.75);
}
</style>