<template>
  <div class="ctr">
    <transition name="fade" mode="out-in">
      <questions
        v-if="questionsAnswered < questions.length"
        :questions="questions"
        :questionsAnswered="questionsAnswered"
        @question-answered="questionAnswered"
      />
      <result v-else :results="results" :totalCorrect="totalCorrect" />
    </transition>

    <button
      type="button"
      class="reset-btn"
      @click.prevent="reset"
      v-if="this.questionsAnswered === questions.length"
    >
      Reset
    </button>
  </div>
</template>

<script>
import Questions from "./components/Questions.vue";
import Result from "./components/Result.vue";

export default {
  name: "App",
  components: {
    Questions,
    Result,
  },
  data() {
    return {
      questionsAnswered: 0,
      totalCorrect: 0,
      questions: [
        {
          q: "Which of the following statements best define Vue.js?",
          answers: [
            {
              text: "Vue.js is an open-source JavaScript library that is used for developing user interfaces.",
              is_correct: false,
            },
            {
              text: "Vue.js is an open-source front-end JavaScript framework used for developing user interfaces.",
              is_correct: true,
            },
            {
              text: "Vue.js is an open-source, cross-platform, JavaScript run-time situation that performs the JavaScript program outside a web browser.",
              is_correct: false,
            },
            {
              text: "Vue.js is a JavaScript library constructed to facilitate HTML DOM tree traversal and administration, event handling, CSS activity, and Ajax.",
              is_correct: false,
            },
          ],
        },
        {
          q: "Why is Vue.js called a progressive framework?",
          answers: [
            {
              text: "Vue.js is called a progressive framework because it is being changed and developed continually.",
              is_correct: true,
            },
            {
              text: "Vue.js is called a progressive framework because it facilitates us to create Dynamic User Interfaces and single-page applications.",
              is_correct: false,
            },
            {
              text: "Vue.js is called a progressive framework because it follows the latest JavaScript standards.",
              is_correct: false,
            },
            {
              text: "All of the above.",
              is_correct: false,
            },
          ],
        },
        {
          q: "What is the main usage of Vue.js?",
          answers: [
            {
              text: "Vue.js is a dynamic JavaScript framework that is frequently used for developing user interfaces.",
              is_correct: true,
            },
            {
              text: "Vue.js is a JavaScript library that makes user interfaces for single-page applications by dividing UI into components.",
              is_correct: false,
            },
            {
              text: "Vue.js uses the MVVM pattern to bind data to certain DOM elements.",
              is_correct: false,
            },
          ],
        },

        {
          q: "Which company invented Vue.js?",
          answers: [
            {
              text: "Facebook",
              is_correct: false,
            },
            {
              text: "Google",
              is_correct: true,
            },
            {
              text: "Oracle",
              is_correct: false,
            },
          ],
        },

        {
          q: "Which of the following is the correct way to install Vue.js in your project?",
          answers: [
            {
              text: "We can install Vue.js by using CDN by including <script> tag in HTML file.",
              is_correct: false,
            },
            {
              text: "We can install Vue.js by using Node Package Manager (NPM).",
              is_correct: false,
            },
            {
              text: "You can install Vue.js using Bower.",
              is_correct: false,
            },
            {
              text: "All of the above.",
              is_correct: true,
            },
          ],
        },
      ],
      results: [
        {
          min: 0,
          max: 5,
          title: "Try again!",
          desc: "Do a little more studying and you may succeed!",
        },
        {
          min: 5,
          max: 5,
          title: "Wow, you're a genius!",
          desc: "Studying has definitely paid off for you!",
        },
      ],
    };
  },
  methods: {
    questionAnswered(is_correct) {
      if (is_correct) {
        this.totalCorrect++;
      }

      this.questionsAnswered++;
    },
    reset() {
      this.questionsAnswered = 0;
      this.totalCorrect = 0;
    },
  },
};
</script>

<style></style>
