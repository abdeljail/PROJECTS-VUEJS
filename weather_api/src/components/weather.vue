<template>
  <div class="hello">
    <div class="box" v-if="data != null && data.cod === 200">
      <div>
        <div>
          {{ data.name + " / " + data.sys.country }}
        </div>
        <div>
          {{ bliudDate() }}
        </div>
      </div>
      <div>{{ data.main.temp }}°c</div>
      <div>
        {{ this.data.weather[0].main }}
      </div>
    </div>
    <div v-else-if="data != null && data.cod === '404'">
      <div>
        <img :src="srcimgNotFound" alt="image is not found city" />
      </div>
      <div>{{ data.message }}</div>
    </div>
    <div v-else>
      <div>
        <img :src="srcImg" alt="image is null" />
      </div>
      <div>plase search city</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Weather",
  data() {
    return {
      srcImg: require("../assets/box.png"),
      srcimgNotFound: require("../assets/page-not-found.png"),
    };
  },
  props: {
    data: Object,
  },
  methods: {
    bliudDate() {
      let d = new Date();
      let months = [
        "January",
        "February",
        "March",
        "April",
        "May",
        "June",
        "July",
        "August",
        "September",
        "October",
        "November",
        "December",
      ];
      let days = [
        "Sunday",
        "Monday",
        "Tuesday",
        "Wednesday",
        "Thursday",
        "Friday",
        "Saturday",
      ];
      let day = days[d.getDay()];
      let date = d.getDate();
      let month = months[d.getMonth()];
      let year = d.getFullYear();
      return `${day} ${date} ${month} ${year}`;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello > div:first-child {
  padding: 10px;
  text-align: center;
}

.hello > div.box:first-child > div:first-child div:last-child {
  margin: 10px 0;
  color: #7c858f;
}
.hello > div.box:first-child > div:nth-child(2) {
  background-color: #fff;
  border-radius: 10px;
  padding: 40px;
  font-size: 24px;
  font-weight: bold;
  margin: 20px 0;
  color: #2c3e50;
}
.hello > div.box:first-child > div:last-child {
  font-size: 30px;
  font-weight: bold;
}

.hello > div:first-child > div:first-child {
  text-align: center;
}
.hello > div:last-child > div:last-child {
  text-transform: capitalize;
  padding: 10px;
  font-weight: bold;
}
img {
  width: 120px;
}
</style>
