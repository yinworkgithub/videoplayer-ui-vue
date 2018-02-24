<template>
    <button v-on:click="() => {say('play')}" class="fullscreen-button"><img :src="fullscreenIcon" /></button>
</template>

<script>
export default {
  name: "fullscreenIcon",
  data() {
    return {
      fullscreenIcon: require("../assets/fullscreen.png")
    };
  },
  methods: {
    say: function(message) {
      console.log(message);
    }
  }
};
</script>

<style lang="scss" scoped>
@import "../css/variables.scss";
.fullscreen-button {
  cursor: pointer;
  margin-left: auto;
  width: 3rem;
  height: 3rem;
}
</style>
