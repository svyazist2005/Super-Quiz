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
    :name="animation" mode="out-in">
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
        // case 0: this.animation="animated wobble";return 'fail';break;
        // case 1: this.animation="animated fadeIn";return 'win';break;
        // case 2: this.animation="animated fadeInUp";return 'quiz';break;
        // case 3: this.animation="animated fadeInUp";return 'quiz';break;
        case 0: this.animation="zoom";return 'fail';break;
        case 1: this.animation="rotate";return 'win';break;
        case 2: this.animation="rotate";return 'quiz';break;
        case 3: this.animation="skew";return 'quiz';break;
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
  animation:rotateIn 0.5s
}

.rotate-leave{
}

.rotate-leave-active{
  animation:rotateOut 0.5s
}


@keyframes rotateIn{
  from{transform:rotate(0deg);}
  to{transform:rotate(360deg);}
}

@keyframes rotateOut{
  from{transform:rotate(360deg);}
  to{transform:rotate(0deg);}
}

.zoom-enter{
}
.zoom-enter-active{
  animation:zoomIn 0.5s
}
.zoom-leave{
}
.zoom-leave-active{
  animation:zoomOut 0.5s
}

@keyframes zoomIn{
  from{transform:scale(1,1);}
  to{transform:scale(1.2,1.2);}
}

@keyframes zoomOut{
  from{transform:scale(1.2,1.2);}
  to{transform:scale(1,1);}
}

.skew-enter{
}
.skew-enter-active{
  animation:skewIn 1s
}
.skew-leave{
}
.skew-leave-active{
  animation:skewOut 1s
}

@keyframes skewIn{
  from{transform:skew(0deg);}
  to{transform:skew(50deg);}
}

@keyframes skewOut{
  from{transform:skew(50deg);}
  to{transform:skew(0deg);}
}

</style>
