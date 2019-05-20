<template>
  <div class="container">
    <div class="row">
      <div class="col-lg-12 col-md-12">
        <div class="card">
          <div class="card-header">
            <h3>What's {{Question}}</h3>
          </div>
          <div class="card-body">
            <div class="row">
              <div class="col-lg-6 col-md-6 col-sm-12 col-xs-12">
                <button class="btn btn-primary" @click="CheckAnswer(0)">{{Opts[0]}}</button>
              </div>
              <div class="col-lg-6 col-md-6 col-sm-12 col-xs-12">
                <button class="btn btn-primary" @click="CheckAnswer(1)">{{Opts[1]}}</button>
              </div>
            </div>
            <div class="row">
              <div class="col-lg-6 col-md-6 col-sm-12 col-xs-12">
                <button class="btn btn-primary" @click="CheckAnswer(2)">{{Opts[2]}}</button>
              </div>
              <div class="col-lg-6 col-md-6 col-sm-12 col-xs-12">
                <button class="btn btn-primary" @click="CheckAnswer(3)">{{Opts[3]}}</button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Correct from "./Correct.vue";
export default {
  data() {
    return {
      Question: "",
      D1: 0,
      D2: 0,
      Sign: "+",
      Ans: 0,
      Opts: [0, 0, 0, 0]
    };
  },
  methods: {
    RamdomNumbers() {
      this.D1 = Math.floor(Math.random() * 200) + 50;
      this.D2 = Math.floor(Math.random() * 200) + 50;
    },
    RandomSign() {
      if (Math.floor(Math.random() * 2) == 0) {
        this.D1 = -1 * this.D1;
      }
      if (Math.floor(Math.random() * 2) == 0) {
        this.D2 = -1 * this.D2;
      }
      if (Math.floor(Math.random() * 2) == 0) {
        this.Sign = "-";
      }
    },
    CalulateAns() {
      if (this.Sign == "-") {
        this.Ans = this.D1 - this.D2;
      } else {
        this.Ans = this.D1 + this.D2;
      }
    },
    RandomOpts() {
      for (let index = 0; index < 4; index++) {
        if (this.Opts[index] == 0) {
          this.Opts.splice(index, 0, Math.floor(Math.random() * this.Ans) + 1);
        }
      }
      this.Opts.splice(Math.floor(Math.random() * 4), 0, this.Ans);
    },
    CreateQues() {
      if (this.D1 < 0) {
        this.Question += "(" + this.D1 + ") " + this.Sign;
      } else {
        this.Question += this.D1 + " " + this.Sign;
      }
      if (this.D2 < 0) {
        this.Question += " (" + this.D2 + ")";
      } else {
        this.Question += " " + this.D2;
      }
    },
    CheckAnswer(index) {
      if (this.Opts[index] == this.Ans) {
        this.$emit("CompChanged", 1);
      } else {
        alert("Wrong answer! Try again");
      }
    }
  },
  created() {
    console.log(this.Comp);
    this.RamdomNumbers();
    this.RandomSign();
    this.CalulateAns();
    this.RandomOpts();
    this.CreateQues();
  },
  components: {
    Correct: Correct
  }
};
</script>

<style scoped>
.container {
  width: 50%;
}
.row {
  padding-top: 10px;
  padding-bottom: 10px;
}
.btn {
  padding-top: 10px;
  padding-bottom: 10px;
  margin-top: 10px;
  margin-bottom: 5px;
}
</style>
