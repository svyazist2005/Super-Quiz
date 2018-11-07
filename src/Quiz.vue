<template id="">
  <div>

    <h3 class="question">Whats {{rand1}}{{rand2}}{{rand3}}</h3>
    <div class="flexcontainer">
      <span class="cells">
        <span class="cell badge " v-for="(el,index) in answer" @click="checkAnswer(index)">{{el}}</span>
      </span>

    </div>

    <!-- <button type="button" name="button" @click="generateQuestion"> GenerateQuestion</button> -->

  </div>
</template>

<script>
export default{
  data:function()
  {return{
    rand1:1,
    rand2:2,
    rand3:3,
    res:0,
    resIndex:0,
    answer:[10,20,30,40]
  }
},
  methods:{
    generateQuestion(){
      this.rand1=Math.floor(Math.random()*10)+Math.floor(Math.random()*10)*10;
      this.rand3=Math.ceil(Math.random()*10)+Math.ceil(Math.random()*10)*10;
      this.rand2=Math.random()*10>5?true:false;
      this.res=this.rand2?this.rand1+this.rand3:this.rand1-this.rand3;
      this.rand2=this.rand2?"+":"-";
      this.resIndex=this.getRandomIntInclusive(0,3);
      this.answer[this.resIndex]=this.res;
    },
    generateFakeAnswers(){
      for(var i=0;i<=3;i++)
      {if (i!=this.resIndex)
        do{this.answer[i]=Math.floor(Math.random()*10)+Math.floor(Math.random()*10)*10;}
        while(this.answer[i]==this.rand1 || this.answer[i]==this.rand2)
      }
    },
    checkAnswer(i){
      if(i==this.resIndex)
      {alert("Correct");
      this.res=true;
      this.gameState=1;
      this.$emit("gameState",this.gameState)
      }
      else
      {alert("Incorrect");
      this.res=false;
      this.gameState=0;
      this.$emit("gameState",this.gameState)
      }
    },
    getRandomIntInclusive(min, max) {
      min = Math.ceil(min);
      max = Math.floor(max);
      return Math.floor(Math.random() * (max - min + 1)) + min; //The maximum is inclusive and the minimum is inclusive
    }
  },
  created(){
    this.gameState=2;
    this.$emit("gameState",this.gameState)
    this.generateQuestion();
    this.generateFakeAnswers();
  }
}
</script>

<style scoped>

h1{
  text-align: center;
}
.question{
  text-align: center;
}
.flexcontainer
{ display: flex;
  justify-content: center;
  align-items: center;
}

.cells{
  display:flex;
  justify-content: space-around;
  flex-wrap: wrap;
  align-items: center;
  width: 400px;
}
.cell{
  font-size: 30px;
  display: flex;
  justify-content: center;
  width:60px;
  padding:5px;
  margin:50px;
  cursor: context-menu;
}

</style>
