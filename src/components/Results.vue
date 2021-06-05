<template>
  <h1>Reaction Time:{{ score }} ms</h1>
  <h1>{{ this.ranking }}</h1>
</template>

<script>
export default {
  props: ["score"],
  methods: {
    makeRanking() {
      if (this.score < 100) {
        this.ranking = "Lighting Fast!";
      } else if (100 <= this.score && this.score < 200) {
        this.ranking = "Pretty Fast";
      } else if (200 < this.score && this.score <= 400) {
        this.ranking = "Kinda Fast";
      } else if (this.score > 800) {
        this.ranking = "Slow";
      }
    },
  },
  data() {
    return {
      ranking: null,
    };
  },
  mounted() {
    this.makeRanking();
  },
};
</script>

<style>
</style>