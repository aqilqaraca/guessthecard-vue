<template>
    <div class="container">
        <h4>Bildiniz</h4>
        <button @click="newGame">Yeni Oyun</button>
    </div>
</template>

<script>
export default {
    methods : {
        newGame(){
            this.$emit("isCorrectEvent","appGameCards")
        }
    }
}
</script>

<style scoped>
    .container{
        width: 100%;
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
        position: absolute;
        top: 0;
        left: 0;
    }
    .container h4{
        text-align: center;
        color: rgb(0, 255, 157);
        font-size: 32px;
    }
    .container button{
        background: transparent;
        border-radius: 10px;
        padding: 20px 40px;
        font-size: 24px;
        color: rgb(0, 255, 157);
        border: 1px solid rgb(0, 255, 157);
        transition: box-shadow 1s;
        cursor: pointer;
    }
    .container button:hover{
        box-shadow: 0 5px 48px #000;
        transition: box-shadow 1s;
    }
</style>