<template>
    <div class="game-area">
        <h1 class="title">
            Kart Oyunu
        </h1>
        <h4 class="description">
            Açıq kartlardan birini seçdikdən sonra qapalı kartı seçin
        </h4>
        <p>{{answer}}</p>
        <div class="container">
            <transition-group name="rotate-all" appear class="container">
                <app-card 
            :class="{'shadow' : selectedCard == card.id}"
            @click.native="selectedCard = card.id" 
            v-for="card in cards" 
            :key="card.id" 
            :card = card
            ></app-card>
            </transition-group>
        </div>
        <div class="container">
            <transition name="rotate" mode="out-in">
                <component :card = "answer" @click.native="showCard(answer)" :is="activeCard">
                </component>
            </transition>
        </div>
    </div>

</template>

<script>
import Card from './Card'
import DefaultCard from './DefaultCard'
export default {
    components : {
        appCard : Card,
        appDefaultCard : DefaultCard
    },
    data(){
        return{
            selectedCard :null,
            answer : {},
            activeCard : "app-DefaultCard",
            cards : [{ id : 1, component : "app-cards", image : "/src/assets/card-1.jpg"},
        { id : 2, component : "app-card", image : "/src/assets/card-2.jpg"},
        { id : 3, component : "app-card", image : "/src/assets/card-3.jpg"},
        { id : 4, component : "app-card", image : "/src/assets/card-4.jpg"},
        { id : 5, component : "app-card", image : "/src/assets/card-5.jpg"}]
        }
        
    },
    created(){
        let answer = Math.ceil(Math.random()*this.cards.length)
        this.answer = this.cards[answer-1]
        console.log(this.answer)
    },
    methods : {
        showCard(answer){
            if(this.selectedCard == null){
                alert("Ilk olaraq bir kart sec")
            }else{
                this.activeCard = answer.component
                setTimeout(()=>{
                if(answer.id == this.selectedCard){
                    this.$emit("isCorrectEvent","app-celebrate")
                }else{
                    this.$emit("isCorrectEvent","app-failer")
                }
                    },1000)
            }
            
        }
    }
}
</script>


<style scoped>
    .title{
        text-align: center;
        font-family: sans-serif;
        color: rosybrown;
    }
    .title span{
        color: mediumpurple;
    }
    .title strong{
        color: darkred;
    }
    .description{
        text-align: center;
        color: grey;
    }
    .container{
        display: flex;
        justify-content: center;
        align-content: center;
        margin-top: 50px;
    }
    .shadow{
    box-shadow: 0 5px 48px #0062ff!important;
    transition: box-shadow .3s;
    }
    .rotate-all-enter-active{
        animation: rotate-all ease-in-out 2s forwards;
    }
    @keyframes rotate-all{
        from{
            transform: rotateY();
        }
        to{
            transform: rotateY(360deg);
        }
    }
    .rotate-enter-active{
        animation: rotate-in .5s ease-in-out  forwards;
    }
    .rotate-leave-acitve{
        animation: rotate-out .5s ease-in-out  forwards;
    }
    @keyframes rotate-in{
        from{
            transform: rotateY(90deg);
        }
        to{
            transform: rotateY(0deg);
        }
    }
    @keyframes rotate-out{
        from{
            transform: rotateY(0deg);
        }
        to{
            transform: rotateY(90deg);
        }
    }
</style>

