<template>
    <div class="container">
        <h4>Bilmediniz</h4>
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
        background: darkorchid;
        position: absolute;
        top: 0;
        left: 0;
    }
    .container h4{
        text-align: center;
        color: #fff;
        font-size: 32px;
    }
    .container button{
        background: transparent;
        border-radius: 10px;
        padding: 20px 40px;
        font-size: 24px;
        color: #fff;
        border: 1px solid #fff;
        transition: box-shadow 1s;
        cursor: pointer;
    }
    .container button:hover{
        box-shadow: 0 5px 48px #000;
        transition: box-shadow 1s;
    }
</style>