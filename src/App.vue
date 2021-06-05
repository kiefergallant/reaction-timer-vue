<template>
  <h1>Reaction Timer</h1>

  <button id="playButton" @click="start" :disabled="isPlaying">
    <h3 id="playButtonText">Play</h3>
  </button>

  <br />
  <br />
  <Box @reactionTime="endGame" v-bind:delay="delay" v-if="isPlaying" />
  <Results v-if="showResults" v-bind:score="score" />
</template>

<script>
import Box from "./components/Box.vue";
import Results from "./components/Results.vue";
export default {
  name: "App",
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      console.log(this.delay);
      this.showResults = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true;
    },
  },
  components: {
    Box,
    Results,
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    };
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
  font-size: 100%;
  font-family: inherit;
  border: 0;
  padding: 0;
}

#playButton {
  background: cornflowerblue;
  border-radius: 10px;
  width: 150px;
  height: 40px;
  margin: 0 auto;
}

#playButtonText {
  margin-top: 8px;
}
</style>
