<template>
  <div
    class="block"
    v-if="showBlock"
    @click="stopTimer"
    :style="{ top: height + 'px', left: width + 'px' }"
  >
    click me
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
      height: document.documentElement.clientHeight,
      width: document.documentElement.clientWidth,
    };
  },
  mounted() {
    setTimeout(() => {
      console.log(this.height, this.width);
      this.height = Math.random() * this.height;
      this.width = Math.random() * this.width;
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
      console.log(this.reactionTime);
      this.$emit("end", this.reactionTime);
    },
  },
};
</script>

<style>
.block {
  position: absolute;
  width: 400px;
  border-radius: 20px;
  background: #0faf87;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>
