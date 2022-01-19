<template>
  <div class="content">
    <header>
      <h1>Build a Weather App in VueJS</h1>
      <p>{{ getname }}</p>
    </header>
    <Search @SearchWeather="SearchWeather" />
    <Weather :data="data" />
  </div>
</template>

<script>
import Weather from "@/components/weather.vue";
import Search from "@/components/searchweather.vue";
export default {
  name: "App",
  data() {
    return {
      data: null,
    };
  },
  components: {
    Weather,
    Search,
  },
  methods: {
    async SearchWeather(city) {
      this.data = await fetch(
        `http://api.openweathermap.org/data/2.5/weather?q=${city}&units=metric&appid=995c8638d33d126bb6e32e96db21aa3a`
      )
        .then((res) => res.json())
        .catch((err) => console.Eroor(err));
    },
  },
  computed: {
    getname() {
      return "";
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}
body {
  background-color: #f7f7f7;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  justify-content: center;
  color: #2c3e50;
  padding: 50px 0;
}
.content {
  padding: 20px 0;
  width: 80%;
  height: 80vh;
  display: flex;
  align-items: center;
  flex-direction: column;
  background-color: #06233a;
  color: #fff;
  border: 2px solid #284262;
  border-radius: 4px;
}
h1 {
  font-size: 4.8vw;
}
</style>
