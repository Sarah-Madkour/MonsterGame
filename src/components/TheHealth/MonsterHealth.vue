<template>
    <base-card class="monster">
      <h1>monster health</h1>
      <div class="health-bar">
        <div class="bar" :style="monsterHealthBar"></div>
      </div>
    </base-card>
</template>

<script>
    export default {
        name : 'MonsterHealth',
        props:['monsterHealthBar' ,],
        data(){
            return{

            }
        }
    }
</script>

<style scoped>
.monster{
    text-transform: capitalize;
}
.health-bar{
    margin-top: 20px;
    width: 100%;
    height: 40px;
    background-color: #f7c3bd;
    border: none;
}
.bar{
  width: 100%;
  height: 100%;
  background-color: darkgreen;
}

</style>