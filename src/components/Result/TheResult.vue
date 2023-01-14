<template>
    <base-card>
    <h1>Game Over!</h1>
    <h2 v-if="winner==='player'">you win!</h2>
    <h2 v-else-if="winner==='monster'">you lose!</h2>
    <h2 v-else>a draw</h2>
    <base-button @click="newGame">New Game</base-button>
    </base-card>
</template>

<script>
import BaseButton from '../UI/BaseButton.vue'
    export default {
        name : 'TheResult',
        props:['newGame' , 'winner'],
        components:{
            BaseButton
        },
       
        
    }
</script>


<style scoped>

h2{
    text-transform: capitalize;
    margin-top: 1rem;
}
</style>