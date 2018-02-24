<template>
    <button v-on:click="() => {say('play')}" class="play-button"><img :src="playIcon" /></button>
</template>

<script>
export default {
  name: "PlayButton",
  data() {
    return {
      playIcon: require("../assets/play.png")
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
.play-button {
  cursor: pointer;
  width: 3rem;
  height: 3rem;
}
</style>
