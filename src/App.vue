<template>
  <div id="app">
    <h2>The Super Quiz</h2>
    <!-- <quiz></quiz>
    <win></win>
    <fail></fail> -->
    <component @gameState="state=$event" :is="componentSelect()"></component>
  </div>
</template>

<script>
import Quiz from './Quiz.vue'
import Win from './Win.vue'
import Fail from './Fail.vue'

export default{
  data:function(){
    return{
      state:2
    }
  },
  components:{
    'quiz':Quiz,
    'win':Win,
    'fail':Fail
  },
  methods:{
    componentSelect(){
      switch (this.state){
        case 0: return 'fail';console.log("fail");break;
        case 1: return 'win';;console.log("win");break;
        default: return 'quiz';console.log("quiz");;
      }
    }
  }
}

</script>

<style scoped>
h2{
  text-align: center;
}
</style>
