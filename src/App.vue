<template>
  <div class="container">
    <div class="row">
      <div class="col-lg-12 col-md-12">
        <h1>The Super Quiz</h1>
        <br>
        <hr>
        <transition name="flip" mode="out-in">
          <component :is="SelectedComp" @CompChanged="CompChanged($event)"></component>
        </transition>
      </div>
    </div>
  </div>
</template>

<script>
import Quiz from "./components/Quiz.vue";
import Correct from "./components/Correct.vue";
export default {
  data() {
    return {
      CompVal: 0,
      SelectedComp: Quiz
    };
  },
  components: {
    Quiz: Quiz,
    Correct: Correct
  },
  methods: {
    CompChanged(val) {
      this.CompVal = val;
      if (this.CompVal == 0) {
        this.SelectedComp = Quiz;
      } else {
        this.SelectedComp = Correct;
      }
    }
  },
  computed: {}
};
</script>

<style scoped>
.container {
  margin-top: 5%;
  text-align: center;
  display: block;
}
le>
    .flip-enter {
        /*transform: rotateY(0deg);*/
    }

    .flip-enter-active {
        animation: flip-in  0.5s ease-out forwards;
    }

    .flip-leave {
        /*transform: rotateY(0deg);*/
    }

    .flip-leave-active {
        animation: flip-out 0.5s ease-out forwards;
    }

    @keyframes flip-out {
        from {
            transform: rotateY(0deg);
        }
        to {
            transform: rotateY(90deg);
        }
    }

    @keyframes flip-in {
        from {
            transform: rotateY(90deg);
        }
        to {
            transform: rotateY(0deg);
        }
    }
</style>
