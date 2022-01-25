<template>
  <NavBar></NavBar>
  <router-view />
</template>

<script>
// @ is an alias to /src
import NavBar from "@/components/NavBar.vue";

export default {
  name: "App",
  components: {
    NavBar,
  },
};
</script>


<style>
* {
  margin: 0;
  padding: 0;
  background-color: #fff8f1;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin: 0 3% 0 3%;
}
a {
  text-decoration: none;
  background-color: inherit;
  color: inherit;
}
</style>
