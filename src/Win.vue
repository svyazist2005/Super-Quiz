<template id="">
<div class="">
  <div class="flexcontainer">
    <h1>Correct!!</h1>
    <button @click="restartGame">Try another one</button>

  </div>
</div>

</template>

<script>

export default{
  methods:{
        restartGame(){
          this.$emit("gameState",2);
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
}
</style>
