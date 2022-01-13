<template>
  <div id="app">
    <header>
      <div id="nav">
        <h1>hello wolrd</h1>
      </div>
    </header>
    <div class="body">
      <todoList />
    </div>
  </div>
</template>
<script>
import todoList from "./components/todoList.vue";
export default {
  name: "app",
  components: {
    todoList,
  },
};
</script>
<style lang="scss">
*{
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
header {
  padding: 10px 0;
  display: flex;
  justify-content: center;
    align-items: center;
  background-color: #eee;
  text-transform: capitalize;
  border-bottom: 5px solid #ddd;
}
#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
