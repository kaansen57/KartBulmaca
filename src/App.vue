<template>
<div id="app">
  <transition-group name="slide" mode="out-in">
    <component
      @answerShow="activeComponent = $event"
      :is="activeComponent"
      key="mainComponent ">
    </component>
    <canvas id="canvas" key="canvas" v-show="activeComponent == 'appCelebrate'"></canvas>
  </transition-group>
</div>

</template>

<script>
  import GamerCard from "./components/GamerCard";
  import Failure from "./components/Failure";
  import Celebrate from "./components/Celebrate";
  export default{
      components:{
          appGameCard : GamerCard,
          appFailure : Failure,
          appCelebrate : Celebrate
      },
      data(){
          return {
              activeComponent : 'appGameCard'
          }
      },
      methods:{

      }
  }
</script>
<style>
 body{
   font-family: sans-serif;
 }
  .slide-enter{}
  .slide-enter-active{
    animation: slide-in .3s ease-in-out forwards;
  }
  .slide-leave{  }
  .slide-leave-active{
    animation: slide-out .3s ease-in-out forwards;
  }

  @keyframes slide-in {
    from {
      transform: translateX(-1000px);
      opacity: 0;
    }
    to{
      transform: translateX(0px);
      opacity: 1;
    }
  }
  @keyframes slide-out {
    from{
      transform: translateX(0px);
      opacity: 1;
    }
    to{
      transform: translateX(1000px);
      opacity: 0;
    }
  }

</style>
