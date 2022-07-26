<template>
  <div id="app">
    <Sidebar />
    <router-view class="view" />
  </div>
</template>
<script>
import Sidebar from "@/components/sidebar.vue";

export default {
  components: {
    Sidebar
  }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Mulish:wght@400;600;700&display=swap');

* {
  text-decoration: none;
  font-family: "Mulish";
}
body {
  background-color: #f7f8fc;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display: flex;
  .view {
    flex: 1;
    margin-left: 255px;
    width: 100%;
    display: flex;
    flex-direction: column;
  }
}
</style>
