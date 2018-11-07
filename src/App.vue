<template>
  <div id="app">
    <h2>The Super Quiz</h2>
    <quiz></quiz>
    <win></win>
    <fail></fail>
  </div>
</template>

<script>
import Quiz from './Quiz.vue'
import Win from './Win.vue'
import Fail from './Fail.vue'

export default{
  components:{
    'quiz':Quiz,
    'win':Win,
    'fail':Fail
  }
}

</script>

<style scoped>
h2{
  text-align: center;
}
</style>
