<template>
  <div class="container">
    <h1>Tebrikler Bildiniz !!!</h1>
    <button @click="newGame">Yeni Oyun</button>
  </div>
</template>

<script>
    export default {
      methods:{
          newGame(){
                this.$emit("answerShow","appGameCard");
          }
      },
        created() {
          const sound  = window.location.pathname + ("src/assets/alkis.mp3");
          let audio  = new Audio(sound);
          audio.play();
        }
    }
</script>
<style scoped>
  .container{
    width:100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    position: absolute;
    left: 0;
    top: 0;
  }
  .container h1{
    text-align: center;
    font-size: 333%;
    color: darkgreen;
  }
  .container button{
    width:200px;
    background-color: #fff;
    color: mediumseagreen;
    border: 1px solid darkgreen;
    height: 50px;
    font-size: 15px;
    border-radius: 5px;
    outline: none;
    transition: all .5s;
    cursor:pointer;
  }
  .container button:hover{
    background-color:darkgreen;
    color:white;
    transition: all .5s;
  }
</style>
