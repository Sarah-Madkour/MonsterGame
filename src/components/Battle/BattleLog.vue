<template>
    <base-card>
      <h1>Battle Log</h1>
      <ul>
        <li v-for="logMessage in logMessages" :key="logMessage">
          <span :class="{'log--player' : logMessage.actionBy==='Player ' , 'log--monster' : logMessage.actionBy==='Monster '}">{{logMessage.actionBy}}</span>
          <span v-if="logMessage.actionType==='Heal '"> heals himself for 
            <span class="log--heal">{{logMessage.actionValue}}</span>
          </span>
          <span v-else>Attacks and deals 
             <span class="log--attack">{{logMessage.actionValue}}</span>
          </span>
          <hr/>
        </li>
      </ul>
    </base-card>
</template>

<script>
    export default {
        name : 'BattleLog',
        props:['logMessages' , 'addLogMessage']
    }
</script>

<style scoped>
h1{
    margin-bottom: 1rem;
}
li{
    list-style: none;
}
hr{
    margin-bottom: 0.5rem;
}
.log--player{
    color: #ae6fae;
    font-weight: 600;
}
.log--monster{
    color: #dbca68;
    font-weight: 600;
}
.log--heal{
    color: #3a753a;
    font-weight: 600;
}
.log--attack{
    color: red;
    font-weight: 600;
}
</style>