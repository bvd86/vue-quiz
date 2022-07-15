<template>
  <div class="ctr">
    <QuizQuestions v-if="questionsAnswered < questions.length"
    :questions="questions"
    :questionsAnswered="questionsAnswered"
    @question-answered="questionAnswered"
    />
    <QuizResult v-else :results="results" :totalCorrect="totalCorrect"/>
    <button type="button" class="reset-btn" @click.prevent="reset"
    v-if="questionsAnswered === questions.length"
   >Reset</button>
  </div>
</template>

<script>
import QuizQuestions from "./components/QuizQuestions.vue";
import QuizResult from "./components/QuizResult.vue";

  export default {
    name: 'App',
    components: {
      QuizQuestions,
      QuizResult,
    },
    data() {
      return {
        questionsAnswered: 0,
        totalCorrect: 0,
        questions: [
        {
          q: 'What is the name of a markup language?',
          answers: [
            {
              text: 'HTML',
              is_correct: true
            },
            {
              text: 'CSS',
              is_correct: false
            },
            {
              text: 'JavaScript',
              is_correct: false
            },
            {
              text: 'Python',
              is_correct: false
            }
          ]
        },
        {
          q: 'What does DB mean in programming?',
          answers: [
            {
              text: 'Double Bass',
              is_correct: false
            },
            {
              text: 'Data Bound',
              is_correct: false
            },
            {
              text: 'Data Base',
              is_correct: true
            },
            {
              text: 'Double Base',
              is_correct: false
            }
          ]
        },
        {
          q: 'What is Full Stack?',
          answers: [
            {
              text: 'Pancakes',
              is_correct: false
            },
            {
              text: 'A Developer',
              is_correct: false
            },
            {
              text: 'Both',
              is_correct: true
            }
          ]
        },
      ],
      results: [
      {
        min: 0,
        max: 2,
        title: "Try again!",
        desc: "Do a little more studying and you may succeed!"
      },
      {
        min: 3,
        max: 3,
        title: "Wow, you're a genius!",
        desc: "Studying has definitely paid off for you!"
      }
      ]
    }
  },
  methods: {
    questionAnswered(is_correct) {
      if(is_correct) {
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
