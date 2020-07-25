<template xmlns:appDefaultCard="http://www.w3.org/1999/html">
  <div class="game-area">

      <h1 class="title"> Kartları<span> Eşleştir </span>  </h1>
      <h4 class="description"> Açık kartlardan birini seçtikten sonra , kapalı olan karta tıklayınız.</h4>
      <div class="container">

        <transition-group name="rotate-all" class="card-container" appear>
          <appCard
            v-for="card in cards"
            :cardImage="card"
            @click.native="selectedCart = card.id"
            :class="{'shadow' : selectedCart == card.id}"
            :key="card.id">
          </appCard>
        </transition-group>

      </div>

    <div class="container">
    <transition name="rotate" mode="out-in" >
      <component
        :cardImage="defaultCardImage"
        @click.native="showCard(defaultCardImage)"
        :is="activeCard">
      </component>
    </transition>
    </div>

  </div>
</template>

<script>
  import Card from "./Card";
  import Default from "./Default";
    export default {
        components:{
            appCard : Card,
            appDefaultCard : Default
        },
        data(){
            return{
                defaultCardImage : null,
                selectedCart:null,
                activeCard : "appDefaultCard",
                cards:[
                    {id :1 ,component :"app-card",image:"/src/assets/card-1.jpg"},
                    {id :2 ,component :"app-card",image:"/src/assets/card-2.jpg"},
                    {id :3 ,component :"app-card",image:"/src/assets/card-3.jpg"},
                    {id :4 ,component :"app-card",image:"/src/assets/card-4.jpg"},
                    {id :5 ,component :"app-card",image:"/src/assets/card-5.jpg"}
                    ]
            }
        },
        created() {
            let answer = Math.ceil(Math.random() * this.cards.length);
            this.defaultCardImage =  this.cards[answer - 1];
        },
        methods:{
            showCard(answer){
                if (this.selectedCart == null){
                    alert("Lütfen Kart Seç");
                }
                else{
                    this.activeCard = answer.component;
                    setTimeout(() => {


                        if (this.selectedCart == answer.id)
                        {
                            this.$emit("answerShow","appCelebrate");
                        }
                        else{
                            this.$emit("answerShow","appFailure");
                        }
                    },1000);
                }

            }
        }
    }
</script>

<style scoped>
  .title {
    text-align: center;
    color: rgb(196, 138, 31);
  }
  .title span {
    color: rgb(168, 22, 22);
  }
  .title strong {
    color: #8b6d86;
  }
  .description {
    color: grey;
    text-align: center;
  }
  .container , card-container {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 10px;
  }
  .shadow{
    box-shadow: 0px 5px 12px #9f1a1b !important;
    transition: box-shadow .5s;
  }
  /****************Açık Kartların Animasyonları******************/

  .rotate-all-enter{}
  .rotate-all-enter-active{
    animation: rotate-all ease-in-out 2s forwards;
  }
  .rotate-all-leave{}
  .rotate-all-leave-active{

  }


  .rotate-enter{}
  .rotate-enter-active{
    animation: rotate-in .3s ease-in-out forwards;
  }
  .rotate-leave{}
  .rotate-leave-active{
    animation: rotate-out .3s ease-in-out forwards;
  }

   @keyframes rotate-all {
     from{
       transform: rotateY(0);
     }
     to{
        transform: rotateY(1080deg);
     }

   }

   @keyframes rotate-in {
    from {
      transform: rotateY(90deg);
    }
    to{
      transform: rotateY(0deg);
    }
   }
   @keyframes rotate-out {
     from{
        transform: rotateY(0);
     }
    to{
        transform: rotateY(90deg);
    }
   }

  /**************************************************************/
</style>
