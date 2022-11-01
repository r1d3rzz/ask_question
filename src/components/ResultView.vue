<template>
  <div>
    <h1>Your Answer is:</h1>
    <div class="viwer fs-3 text-primary">{{ result }}</div>
    <hr />
    <div class="animate__animated animate__bounceIn animate__delay-1s">
      <button class="btn" @click="decidedAgain">Decide Again</button>
      <button class="btn" @click="goBack">Ask new Question</button>
    </div>
  </div>
</template>

<script>
export default {
  props: ["result"],
  methods: {
    goBack() {
      this.$emit("changePosition", 0);
    },
    decidedAgain() {
      this.$emit("showResult");
    },
  },
  mounted() {
    this.decidedAgain();
  },
};
</script>

<style>
</style>