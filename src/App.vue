<template>
  <div>
    <the-header></the-header>
   <monster-health :monsterHealthBar="monsterHealthBar"></monster-health>
    <player-health :playerHealthBar="playerHealthBar"></player-health>
    <the-result v-if="winner" :newGame="newGame" :winner="winner"></the-result>
    <div class="btns" v-else>
      <base-button  @click="attackMonster">attack</base-button>
      <base-button  :disabled="mayUseSpecialAttack" @click="specialAttack" >special attack</base-button>
      <base-button  @click="heal" :disabled="mayUseHeal">heal</base-button>
      <base-button @click="surrender">surrender</base-button>
    </div>
    <battle-log :logMessages="logMessages" :addLogMessage="addLogMessage"></battle-log>
  </div>
</template>



<script>

function getRandomValues(min,max){
  return Math.floor(Math.random() * (max-min) + min)
}

import TheHeader from './components/Layout/TheHeader.vue'
import TheResult from './components/Result/TheResult.vue'
import MonsterHealth from './components/TheHealth/MonsterHealth.vue'
import PlayerHealth from'./components/TheHealth/PlayerHealth.vue'
import BattleLog from './components/Battle/BattleLog.vue'


export default {
  name: 'App',
  components: {
    TheHeader,
    MonsterHealth,
    PlayerHealth,
    TheResult,
    BattleLog

   },
   data(){
    return{
      monsterHealth:100,
      playerHealth:100,
      winner:null,
      currentRound : 0,
      logMessages:[]
    }
   },
   watch:{
        monsterHealth(value){
        if(value<=0 && this.playerHealth <=0){
            this.winner='draw'
        }else if(value<=0){
            this.winner = 'player'
        }
        },
        playerHealth(value){
        if(value<=0 && this.monsterHealth<=0){
            this.winner='draw'
        }else if(value<=0){
            this.winner='monster'
        }
        }
    },
   
   computed:{
    monsterHealthBar(){
      if(this.monsterHealth <=0){
        return {width :'0%'}
      }else{
        return {width : this.monsterHealth + '%'}
      }
    },
    playerHealthBar(){
      if(this.playerHealth <=0){
        return {width : '0%'}
      }else {
        return{width : this.playerHealth + '%'}
      }
    },
    mayUseSpecialAttack(){
      return this.currentRound % 3 !==0
    },
    mayUseHeal(){
      return this.currentRound % 2 !==0
    }
   },
  
   methods:{
    newGame(){
      this.currentRound=0,
      this.playerHealth=100,
      this.monsterHealth=100,
      this.winner=null,
      this.logMessages=[]
    },
    attackMonster(){
      this.currentRound++
      const attackValue = getRandomValues(12,5);
      this.monsterHealth -= attackValue;
      this.attackPlayer();
      this.addLogMessage('Player ' , 'Attack ' , attackValue)
    },
    attackPlayer(){
      const attackValue = getRandomValues(25,7);
      this.playerHealth -= attackValue;
      this.addLogMessage('Monster ' , 'Attack ' , attackValue)
    },
    specialAttack(){
      this.currentRound++;
      const specialAttackValue = getRandomValues(25,20);
      this.monsterHealth -= specialAttackValue
      this.attackPlayer();
      this.addLogMessage('Player ' , 'PpecialAttack ' , specialAttackValue)
    },
    heal(){
      this.currentRound++;
      const healValue = getRandomValues(25,10);
      this.playerHealth +=healValue;
      if(this.playerHealth +healValue >=100){
        this.playerHealth =100
      }else{
        this.playerHealth += healValue
      }
      this.attackPlayer();
      this.addLogMessage('Player ' , 'Heal ' , healValue)
    },
    surrender(){
      this.winner='monster'
    },
    addLogMessage(who , what , value){
      this.logMessages.unshift({
        actionBy : who,
        actionType : what ,
        actionValue : value
      })
    }
   }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  
}*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
.btns{
  width:700px;
  margin: auto;
  display: flex;
  justify-content: space-between;
  flex-wrap:wrap;
}




</style>
