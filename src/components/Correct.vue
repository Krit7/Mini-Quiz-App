<template>
  <div class="container">
    <div class="row">
      <div class="col-lg-12 col-md-12">
        <div class="card bg-success bg">
          <div class="card-header">
            <h1>That's Correct</h1>
          </div>
          <div class="card-body">
            <button class="btn btn-primary" @click="CompChanged">Next Question</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
    methods:{
        CompChanged(){
            this.$emit("CompChanged", 0);
        }
    }
};
</script>

<style scoped>
.container {
  width: 50%;
}
.card-header{
    background-color: rgb(154, 207, 154);
    color: green;
}
.card-body{
    background-color: rgb(154, 207, 154);
}
.btn{
    margin: 40px 0;
}

</style>
