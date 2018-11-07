<template id="">
<div class="">
  <div class="flexcontainer">
    <h1>Correct!!</h1>
    <div class="buttons ">
      <button class="btn btn-primary" @click="restartGame">Try another one</button>
      <button class="btn btn-danger" @click="resetGame">Reset game</button>
    </div>
</div>
</div>

</template>

<script>

export default{
  methods:{
        restartGame(){
          this.$emit("gameState",2);
        },
        resetGame(){
          this.$emit("gameState",3);
        }
  }
}
</script>

<style scoped>

.flexcontainer
{ display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
h1{
  color:green;
    font-family: monospace;
}

.buttons{
  display:inline-block;

}
</style>
