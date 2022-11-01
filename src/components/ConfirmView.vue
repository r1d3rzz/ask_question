<template>
  <div>
    <h1>Your Question is:</h1>
    <div class="viwer">{{ question }}</div>
    <hr />
    <button class="btn" @click="goToResultView">Decide it</button>
    <button class="btn" @click="goBack">Ask new Question</button>
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