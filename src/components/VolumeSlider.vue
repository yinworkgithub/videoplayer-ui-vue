<template>
<div class="volume-slider-container active" v-bind:class="{ active: isActive }"  @mouseenter="volumeSliderHoverInHandler" @mouseleave="volumeSliderHoverOutHandler" >
    <button class="volume-button"><img :src="volumeIcon" /></button>

    <div class="volume-slider" ref="volumeSlider" @click="volumeSliderClickHandler" @mousedown="startDragSliderHandler" @mouseup="stopDragSliderHandler">
      <div class="volume-slider-control">
        <div class="volume-slider-progress" :style="{ width: `${volumeProgressPercentage}%` }">
          <div class="volume-slider-handler"></div>
        </div>
      </div>
    </div>

</div>
</template>

<script>
export default {
  name: "VolumeSlider",
  data: () => ({
    volumeIcon: require("../assets/volume.png"),
    isActive: false,
    volumeProgressPercentage: 50
  }),
  computed: {},
  methods: {
    volumeSliderHoverInHandler() {
      console.log("volumeHoverIn");
      clearTimeout(this.volumeHoverTimout);
      this.isActive = true;
    },
    volumeSliderHoverOutHandler() {
      console.log("volumeHoverOut");
      this.volumeHoverTimout = setTimeout(() => {
        this.isActive = false;
      }, 1000);
    },
    volumeSliderClickHandler(event) {
      const volumePercentage = this.getElementPercentage(
        event,
        this.$refs.volumeSlider
      );
      this.setVolumeSliderProgress(this.validateVolume(volumePercentage));
    },
    setVolumeSliderProgress(volumePercentage) {
      this.volumeProgressPercentage = volumePercentage;
      console.log("volumePercentage: ", volumePercentage);
    },
    startDragSliderHandler() {
      document.addEventListener("mousemove", this.sliderHandlerMoveHandler);
      document.addEventListener("mouseup", this.stopDragSliderHandler);
    },
    stopDragSliderHandler() {
      document.removeEventListener("mousemove", this.sliderHandlerMoveHandler);
      document.removeEventListener("mouseup", this.stopDragSliderHandler);
    },
    sliderHandlerMoveHandler(event) {
      const volumePercentage = this.getElementPercentage(
        event,
        this.$refs.volumeSlider
      );
      this.setVolumeSliderProgress(this.validateVolume(volumePercentage));
    },
    getElementPercentage(event, element) {
      const rect = element.getBoundingClientRect();
      return (event.clientX - rect.left) / rect.width * 100;
    },
    validateVolume(volumePercentage) {
      if (volumePercentage < 0) {
        volumePercentage = 0;
      } else if (volumePercentage > 100) {
        volumePercentage = 100;
      }
      return volumePercentage;
    }
  }
};
</script>

<style lang="scss" scoped>
@import "../css/variables.scss";
.volume-slider-container {
  display: flex;
  width: 3rem;
  position: relative;
  // overflow: hidden;
  .volume-button {
    cursor: pointer;
    width: 3rem;
    height: 3rem;
  }

  .volume-slider {
    // outline: 1px solid red;
    width: 6rem;
    position: relative;
    .volume-slider-control {
      background-color: $grey;
      position: absolute;
      top: 50%;
      height: 0.2rem;
      margin-top: -0.1rem;
      width: 100%;
      .volume-slider-progress {
        height: 100%;
        background: $pink;
        position: relative;
      }

      .volume-slider-handler {
        position: absolute;
        right: 0;
        top: -0.7rem;
        height: 1.5rem;
        width: 0.3rem;
        background-color: $white;
      }
    }
  }

  &.active {
    width: 9rem;
    transition: width 0.1s;
  }
}
</style>
