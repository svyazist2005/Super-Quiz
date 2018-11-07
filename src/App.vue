<template>
  <div id="app">
    <h2>The Super Quiz</h2>
    <quiz></quiz>
    <win></win>

  </div>
</template>

<script>
import Quiz from './Quiz.vue'
import Win from './Win.vue'
export default{
  components:{
    'quiz':Quiz,
    'win':Win
  }
}

</script>

<style scoped>
h2{
  text-align: center;
}
</style>
