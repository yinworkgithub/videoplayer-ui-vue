<template>
  <div class="video-player-container">
    <img src="http://img.izismile.com/img/img6/20130327/640/the_simpsons_versions_of_wellknown_movie_moments_640_24.jpg" class="video-player visible" />
    <BottomBar/>
  </div>
</template>

<script>
import BottomBar from "./components/BottomBar.vue";
export default {
  name: "VideoPlayer",
  components: {
    BottomBar
  },
  props: {
    msg: String
  }
};
</script>

<style lang="scss" scoped>
@import "./css/variables.scss";
.video-player-container {
  width: 50rem;
  height: 30rem;
  background-color: $grey;
  display: flex;
  flex-direction: column;
  overflow: hidden;
  position: relative;
  .video-player {
    cursor: pointer;
    width: 100%;
    height: 100%;
    opacity: 0;
    &.visible {
      opacity: 1;
      transition: opacity 1s ease-out 0.8s;
    }
  }
}
</style>
