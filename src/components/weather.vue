<template>
  <div id="weather">
    <h2>{{city}}</h2>
    <div id="weather-now">
      <p>Now</p>
      <p>{{weatherNow.main.temp}}C</p>
      <p>{{weatherNow.weather[0].main}}</p>
      <p>Minimum: {{weatherNow.main.temp_min}}C</p>
      <p>Maximum: {{weatherNow.main.temp_max}}C</p>
      <p>Humidity: {{weatherNow.main.humidity}}%</p>
    </div>
    <div id="weathe-forecast"></div>
    <p>Forecast</p>
    <p>{{weatherForecast}}</p>
  </div>
</template>

<script>
import KeysFile from "../apiKeys.js";
export default {
  data() {
    return {
      city: "Amsterdam,NL",
      key: KeysFile.keys.weatherKey,
      weatherNow: {},
      weatherForecast: {}
    };
  },
  methods: {},
  created() {
    this.$http
      .get(
        `http://api.openweathermap.org/data/2.5/weather?q=${this.city}&APPID=${
          this.key
        }&units=metric`
      )
      .then(data => data.json())
      .then(data => (this.weatherNow = data))
      .catch(error => console.error(error));

    this.$http
      .get(
        `http://api.openweathermap.org/data/2.5/forecast?q=${this.city}&APPID=${
          this.key
        }&units=metric`
      )
      .then(data => data.json())
      .then(data => (this.weatherForecast = data))
      .catch(error => console.error(error));
  }
};
</script>

<style scoped>
</style>
