<template>
    <base-card>
        <h1>Player Health</h1>
        <div class="health-bar">
            <div class="bar" :style="playerHealthBar"></div>
        </div>
    </base-card>
</template>

<script>
    export default {
        name : 'PlayerHealth',
        props:['playerHealthBar']
        
    }
</script>

<style scoped>
.health-bar{
    width: 100%;
    height: 40px;
    background-color: #f7c3bd;

}
.bar{
    width: 100%;
    height :100%;
    background-color: darkgreen;
}
</style>