<template>
  <h1>Reaction Timer</h1>
  <button :disabled="isPlaying" @click="start">Start</button>
  <button :disabled="!isPlaying" @click="stop">Stop</button>
  <Block v-if="isPlaying" />
</template>

<script>
import Block from "./components/Block.vue";
export default {
  name: "App",
  components: { Block },
  data() {
    return {
      isPlaying: false,
      delay: null,
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 3000;
      this.isPlaying = true;
    },
    stop() {
      this.isPlaying = false;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
button {
  margin-left: 10px;
}
</style>
