<template>
  <div id="app">
    <VideoPlayer msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import "./css/reset.scss";
import VideoPlayer from "./VideoPlayer.vue";

export default {
  name: "app",
  components: {
    VideoPlayer
  }
};
</script>

<style lang="scss" >
@import "./css/variables.scss";
#app {
  display: flex;
  // justify-content: center;
  align-items: center;
  // * {
  //   outline: 1px solid red;
  // }
}
</style>
