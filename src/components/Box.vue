<template>
  <div @click="stopTimer" v-if="showBlock" id="box">
    <h1>Click Me</h1>
  </div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 1;
      }, 1);
    },
    stopTimer() {
      clearInterval(this.timer);
      console.log(this.reactionTime);
      this.$emit("reactionTime", this.reactionTime);
    },
  },
};
</script>

<style>
#box {
  margin: 0 auto;
  display: flex;
  justify-content: center;
  flex-direction: column;
  height: 400px;
  background: cornflowerblue;
  width: 20em;
  height: 20em;
  border-radius: 30px;
}
</style>