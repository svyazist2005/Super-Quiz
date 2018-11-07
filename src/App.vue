<template>
  <div id="app">
    <hr>
    <h1>The Super Quiz</h1>
    <hr>
    <transition
    :enter-active-class="animation" mode="out-in">
    <component @gameState="state=$event" :is="componentSelect()"></component>
    </transition>
  </div>
</template>

<script>
import Quiz from './Quiz.vue'
import Win from './Win.vue'
import Fail from './Fail.vue'

export default{
  data:function(){
    return{
      state:2,
      animation:'animated fadeInDown'
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
        case 0: this.animation="animated wobble";return 'fail';break;
        case 1: this.animation="animated fadeIn";return 'win';break;
        default: this.animation="animated fadeInUp";return 'quiz';break;
      }
    }
  }
}

</script>

<style scoped>
h1{
  font-size: 50px;
  font-family: monospace;
  color:white;
  text-align: center;
  opacity: 0.6;
  background-color: green;
}
</style>
