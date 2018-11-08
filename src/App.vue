<template>
  <div id="app">
    <hr>
    <h1>The Super Quiz</h1>
    <hr>
    <h2>Wins:{{score[1]}} Fails:{{score[0]}}</h2>
    <hr>
    <!-- <transition
    :enter-active-class="animation" mode="out-in"> -->
    <transition
    name="rotate" mode="out-in">
    <component @gameState="state=$event;state!=3?score[state]++:score=[0,0]" :is="componentSelect()"></component>
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
      score:[0,0],
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
        case 2: this.animation="animated fadeInUp";return 'quiz';break;
        case 3: this.animation="animated fadeInUp";return 'quiz';break;
      }
    }
  }
}

</script>

<style scoped>

h1,h2{
  font-size: 50px;
  font-family: monospace;
  color:white;
  text-align: center;
  opacity: 0.6;
  background-color: green;
}
h2{
  font-size: 30px;
  color:yellow;
}

.rotate-enter{
}
.rotate-enter-active{
  animation:rotateIn 1s
}

.rotate-leave{
}

.rotate-leave-active{
  animation:rotateOut 1s
}


@keyframes rotateIn{
  from{transform:rotate(0deg);}
  to{transform:rotate(90deg);}
}

@keyframes rotateOut{
  from{transform:rotate(90deg);}
  to{transform:rotate(0deg);}
}



</style>
