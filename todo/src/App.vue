<template>
  <div id="app">
    <Create />
  </div>
</template>

<script>
import Create from "./components/Create.vue";

export default {
  name: "app",
  components: {
    Create
  }
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  line-height: 1.4rem;
  background-color: #f1f2f6;
}
a {
  text-decoration: none;
}
</style>
