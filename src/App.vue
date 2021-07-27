<template>
  <div id="app">
    <mynav />
    <router-view />
  </div>
</template>

<script>
import mynav from "./components/mynav";
export default {
  components: {
    mynav,
  },
};
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
