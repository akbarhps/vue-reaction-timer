<template>
  <div class="backdrop" @click.self="closeResult">
    <div class="block" @click="stopTimer" v-if="showBlock">click me</div>
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
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("endGame", this.reactionTime);
    },
  },
};
</script>

<style>
.backdrop {
  top: 0;
  position: fixed;
  background: black;
  width: 100%;
  display: flex;
  height: 100%;
  align-content: center;
}
.block {
  width: 400px;
  border-radius: 20px;
  background: black;
  color: white;
  border: 1px white solid;
  text-align: center;
  padding: 100px 0;
  margin: auto;
  cursor: pointer;
}
</style>