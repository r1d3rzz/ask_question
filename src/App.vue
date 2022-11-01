<template>
  <div class="container">
    <component
      :is="screen[position]"
      @changePosition="changePosition"
      @askQuestion="askQuestion"
      :question="question"
    />
  </div>
</template>

<script>
import InitialView from "./components/InitialView";
import ResultView from "./components/ResultView";
import ConfirmView from "./components/ConfirmView";
import "./assets/style.css";

export default {
  components: { InitialView, ConfirmView, ResultView },
  data() {
    return {
      screen: ["InitialView", "ConfirmView", "ResultView"],
      question: "",
      position: 0,
    };
  },

  methods: {
    changePosition(value) {
      this.position = value;
    },

    askQuestion(value) {
      this.question = value;
    },
  },
};
</script>

<style>
</style>