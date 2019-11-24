<template>
  <div>
    <p class="msg">{{msg}}</p>
  </div>
</template>


<script>
  export default{ //配置对象
    data(){
      return {
        msg: "Hello Vue Component"
      }
    }
  }
</script>


<style>
  .msg {
    font-size: 30px;
    color: blue;
  }
</style>
