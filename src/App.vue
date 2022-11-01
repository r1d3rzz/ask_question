<template>
  <div class="container">
    <transition name="fade" appear mode="out-in">
      <component
        :is="screen[position]"
        @changePosition="changePosition"
        @askQuestion="askQuestion"
        :question="question"
        :result="result"
        @showResult="showResult"
      />
    </transition>
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
      list: [
        "Yes",
        "No",
        "Maybe",
        "Not sure..try again",
        "Ask a friend",
        "Call the police",
      ],
      screen: ["InitialView", "ConfirmView", "ResultView"],
      question: "",
      result: "",
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

    getRandomValue() {
      return this.list[Math.floor(Math.random() * this.list.length)];
    },

    generateResult() {
      let rand = this.getRandomValue();
      if (rand !== "") {
        while (rand === this.result) {
          rand = this.getRandomValue();
        }
      }
      this.result = rand;
    },

    showResult() {
      this.generateResult();
    },
  },
};
</script>

<style>
.fade-enter-from {
  opacity: 0;
}
.fade-enter-active {
  transition: 0.5s;
}
.fade-enter-to {
  opacity: 1;
}

.fade-enter-from {
  opacity: 1;
}
.fade-enter-active {
  transition: 0.5s;
}
.fade-enter-to {
  opacity: 0;
}
</style>