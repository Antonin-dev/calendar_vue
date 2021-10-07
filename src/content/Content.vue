<template>
  <div id="content" class="bg-blue-200  min-h-screen w-full min-w-screen">
    <div class="w-full container-title-weather flex justify-around">
      <h1 class="text-center text-3xl p-4">Calendar</h1>
      <WeatherDisplay />
    </div>
    <div id="content-card" class="flex flex-wrap justify-around">
      <Card :key="index" v-for="(date, index) in dates" :date="date"/>
    </div>
  </div>
</template>

<script>
import Card from "../components/Card.vue";
import WeatherDisplay from "../components/WeatherDisplay.vue";
let calendar = {
  date : []
}

// Counter day for calendar
for (let i = 1 ; i <= 31 ; i++){
  calendar.date.push({
    day: i
  })
}
export default {
  name: "Content",
  components: {WeatherDisplay, Card},
  data() {
    return {
      dates: calendar.date,
    }
  },
  // mounted() {
  //   axios.get("api.openweathermap.org/data/2.5/weather?q=Montpellier&appid=b130dcc54270096a657437a5cdb60cd9").then(response => (this.weather = response))
  //
  // }
}


</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2? family= Danse+Script & display=swap');
h1{
  font-family : 'Dancing Script', cursif ;
}
</style>
