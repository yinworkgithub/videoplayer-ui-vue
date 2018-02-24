<template>
  <div class="bottom-bar">
      <!-- {{ playIcon }} -->
    <div class="progress-bar">
    </div>

    <div class="control-bar">
      <PlayButton />
      <VolumeSlider />
      <FullscreenButton />
    </div>

  </div>
</template>

<script>
import PlayButton from "./PlayButton.vue";
import VolumeSlider from "./VolumeSlider.vue";
import FullscreenButton from "./FullscreenButton.vue";

export default {
  name: "BottomBar",
  components: {
    PlayButton,
    FullscreenButton,
    VolumeSlider
  },
  props: {
    msg: String
  }
};
</script>

<style lang="scss" scoped>
@import "../css/variables.scss";
.bottom-bar {
  width: 100%;
  z-index: 1;
  // bottom: -2rem;
  position: absolute;
  bottom: 0;
  .progress-bar {
    background: $purple;
    height: 0.5rem;
  }
  .control-bar {
    height: 3rem;
    background-color: $greyOpacity05;
    display: flex;
    flex-direction: row;
    width: 100%;
  }
  &.active {
    bottom: 0;
    transition: bottom 1s ease-out;
  }
}
</style>
