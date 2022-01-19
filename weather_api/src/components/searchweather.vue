<template>
  <div>
    <input placeholder="enter city" v-model="nameSearch" type="search" name="search" id="search" />
    <button @click="$emit('SearchWeather', nameSearch)">search</button>
  </div>
</template>

<script>
export default {
  name: "Search",
  data() {
    return {
      nameSearch: "",
    };
  },
};
</script>

<style scoped>
div {
  padding: 0 10px;
  width: 100%;
  display: flex;
}
input,
button {
  border: none;
  outline: none;
  padding: 10px 15px;
}
input {
  width: 70%;
}
input:focus{
  border: 1px solid #05564f;
}
button {
  width: 30%;
  background-color: #05564f;
  color:#fff;
  cursor: pointer;
}
</style>
