<template>
  <div class="full">
    <div id="app" class="container-fluid">
      <div class="row">
        <Home></Home>
        <Characters></Characters>
      </div>
    </div>
  </div>
</template>

<script src="https://code.jquery.com/jquery-3.2.1.min.js"></script>

<script>
import Home from "./components/Home.vue";
import Characters from "./components/Characters.vue";

export default {
  name: "App",

  components: {
    Home,
    Characters,
  },
};
</script>

<style lang="scss">
@import "../node_modules/ag-grid-community/dist/styles/ag-grid.css";
@import "../node_modules/ag-grid-community/dist/styles/ag-theme-balham.css";

.container-fluid {
  margin-top: 1%;
  padding: 20px;
}

h1 {
  color: black;
  font-size: 400%;
}
</style>
