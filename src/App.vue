<template>
    <transition-group name="slide" mode="out-in">
        <component key="maincomp" @isCorrectEvent = "activeComponent = $event" :is="activeComponent">
        
    </component>
    <canvas v-show="activeComponent == 'app-celebrate'" id="canvas" key="canvas"></canvas>
    </transition-group>
</template>
<script>
import Card from './Components/Card'
import Celebrate from './Components/Celebrate'
import DefaultCard from './Components/DefaultCard'
import Failer from './Components/Failer'
import GameCards from './Components/GameCards'

export default {
    components : {
        appCard : Card,
        appCelebrate : Celebrate,
        appDefaultCard : DefaultCard,
        appFailer : Failer,
        appGameCards : GameCards
    },
    data(){
        return{
            activeComponent : "appGameCards"
        }
    }
}
</script>
<style scoped>
    .slide-enter-active{
        animation: slide-in .3s ease-out forwards;
    }
    .slide-leave-active{
        animation: slide-out .3s ease-out forwards;;
    }
    @keyframes slide-in{
        from{
            transform: translateX(-1000px);
            opacity: 0;
        }
        to{
            transform: translateX(0);
            opacity: 1;
        }
    }
    @keyframes slide-out{
        from{
            transform: translateX(0);
            opacity: 1;
        }
        to{
            transform: translateX(1000px);
            opacity: 0;
        }
    }
</style>
