<template>
  <div>
    <h1>Your Question is:</h1>
    <div class="viwer fs-3">{{ question }}?</div>
    <hr />
    <div class="animate__animated animate__bounceIn animate__delay-1s">
      <button class="btn" @click="goToResultView">Decide it</button>
      <button class="btn" @click="goBack">Ask new Question</button>
    </div>
  </div>
</template>

<script>
export default {
  props: ["question"],
  methods: {
    goBack() {
      this.$emit("changePosition", 0);
    },
    goToResultView() {
      this.$emit("changePosition", 2);
    },
  },
};
</script>

<style>
</style>