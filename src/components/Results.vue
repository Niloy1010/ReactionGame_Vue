<template>
  <p>Reaction Time:</p>
  <h1>{{ this.result }} ms</h1>
  <p class="rank">{{ fastCalculation }}</p>
</template>

<script>
export default {
  props: ["result"],
  data() {
    return {
      fastCalculation: "good",
    };
  },
  mounted() {
    if (this.result < 300) this.fastCalculation = "Over 9000!!";
    else if (this.result < 550) this.fastCalculation = "Not Bad!!";
    else this.fastCalculation = "You'll never be a ninja";
  },
};
</script>

<style>
.rank {
  font-size: 1.4em;
  color: #0faf87;
  font-weight: bold;
}
</style>
