<template>
  <div>
    <h1>Ask a Question</h1>
    <form @submit.prevent="askQuestion">
      <input type="text" class="form-control" v-model="question" />
      <div v-if="question">
        <button class="btn btn-dark animate__animated animate__fadeIn">
          Ask
        </button>
      </div>

      <div class="error" v-if="error">You question is to short</div>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      question: "",
      error: false,
    };
  },

  methods: {
    askQuestion() {
      if (this.question.length <= 3) {
        return this.$emit("handleToast", {
          type: "error",
          message: "Your Question is Too Short",
        });
      } else if (this.question.length >= 50) {
        return this.$emit("handleToast", {
          type: "error",
          message: "Your Question is Too Long",
        });
      } else {
        this.$emit("changePosition", 1);
        this.$emit("askQuestion", this.question);
      }
    },
  },
};
</script>

<style>
</style>