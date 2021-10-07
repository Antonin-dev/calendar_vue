<template>
<div class="w-2/4 bg-green-400 rounded-3xl p-3 flex justify-around items-center opacity-80">
  <p>Temperature actuelle : {{dataWeather.actualTemperature}} °C</p>
  <p>Ciel : {{dataWeather.sky}}</p>
</div>
</template>

<script>
export default {
  name: "WeatherDisplay",
  data(){
    return {
      dataWeather: {
        actualTemperature: null,
        sky: null,

      },
    }
  },
  methods:{
    async fetchApi () {
        const datas = await fetch("https://api.openweathermap.org/data/2.5/weather?q=Montpellier&units=metric&appid=b130dcc54270096a657437a5cdb60cd9&lang=fr", {method:"GET"})
        const dataJson = await datas.json();
        this.dataWeather.actualTemperature = Math.round(dataJson.main.temp);
        this.dataWeather.sky = dataJson.weather[0].description;
    }
  },
  mounted() {
    this.fetchApi();
  }
}
</script>

<style scoped>

</style>
