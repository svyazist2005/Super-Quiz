<template id="">
  <div>

    <h3 class="question">Whats {{rand1}}{{rand2}}{{rand3}}</h3>
    <div class="flexcontainer">
      <span class="cells">
        <span class="cell badge " >{{answer[0]}}</span>
        <span class="cell badge " >{{answer[1]}}</span>
        <span class="cell badge " >{{answer[2]}}</span>
        <span class="cell badge " >{{answer[3]}}</span>
      </span>

    </div>

  </div>
</template>

<script>
export default{
  data:function()
  {return{
    rand1:1,
    rand2:2,
    rand3:3,
    answer:[10,20,30,40]
  }
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
