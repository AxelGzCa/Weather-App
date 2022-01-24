<template>
  <div v-if="result" class="About">
    <header>
      <p><b>{{result.name}}</b></p>
    </header>
    <img :src="'http://openweathermap.org/img/w/'+result.weather[0].icon+'.png' " alt="">
    <p>{{ result.weather[0].description }}</p>
    <p>Temp: {{ result.main.temp }}</p>
    <p>Degrees: {{ result.wind.deg }}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data: () => ({
    result: null,
  }),
  created() {
      axios
        .get(
            "https://api.openweathermap.org/data/2.5/weather?q=playa%20del%20carmen&APPID=ef78334d531d4ede0c95da239412f022")
        .then((result) => {
          this.result = result.data;
          console.log(result.data);
        });
  }
};
</script>