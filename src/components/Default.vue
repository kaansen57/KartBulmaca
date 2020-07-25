<template>
  <div>
    <div class="card" >
    </div>
  </div>
</template>

<script>
    export default {

    }
</script>

<style scoped>
  .card{
    width:200px;
    height: 232px;
    border-radius: 5px;
    border: 1px solid #666;
    transition: box-shadow .5s;
    /*  margin-left:15px ; */
    background-image: url("../assets/default-kart.jpg");
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
  }
  .card:hover{
    box-shadow: 0px 5px 48px #666;
    transition: box-shadow .5s;
  }
  .card img{
    width: 100%;
    height: 100%;
  }
</style>
