<template>
  <Header />
  <div v-if="playerHealth1 > 0 && monsterHealth1 > 0">
  <MonsterHealth  :monsterHealth1="monsterHealth1"/>
  <PlayerHealth :playerHealth1="playerHealth1"/>
  <SpecialButtons @attacked="attackMonster" @healed="healPlayer" @special-attacked="specialAttack"
    :currentRound="currentRound" @surrender="loseGame"/>
  </div>
  <div v-else-if="monsterHealth1 < 1">
    <GameWin @start-new="resetGame" />
  </div> 
  <div v-else-if="playerHealth1 < 1">
    <LostScreen @start-new="resetGame" />
  </div> 
  <BattleLog :logs="logs"/>
</template>

<script>
import Header from './components/Header';
import MonsterHealth from './components/MonsterHealth';
import PlayerHealth from './components/PlayerHealth';
import SpecialButtons from './components/SpecialButtons';
import BattleLog from './components/BattleLog';
import LostScreen from './components/LostScreen';
import GameWin from './components/GameWin';

export default {
  name: 'App',
  components: {
    Header,
    MonsterHealth,
    PlayerHealth,
    SpecialButtons,
    BattleLog,
    LostScreen,
    GameWin
  },
  data(){
    return{
      monsterHealth1: 100,
      playerHealth1: 100,
      currentRound: 0,
      logs: [] 
    }
  },
  methods:{
    attackMonster(){
      const attackValue = this.getRandomValue(5, 12);
      this.monsterHealth1 = this.monsterHealth1 - attackValue;
     if(this.monsterHealth1 < 0) this.monsterHealth1 = 0;
     //console.log(this.monsterHealth1);
     this.currentRound +=1;
     const newLog = {
       type: 'playerAttack',
       message: 'You attecked for ' + attackValue + ' damage'
     }
     this.logs.unshift(newLog);
      this.attackPlayer();
    },
    attackPlayer(){
      const attackValue = this.getRandomValue(8, 15);
      this.playerHealth1 -= attackValue;
      const newLog = {
            type: 'monsterAttack',
            message: 'Monster attecked for ' + attackValue + ' damage'
          }
          this.logs.unshift(newLog);
      if(this.playerHealth1 < 0) this.playerHealth1 = 0;
      // console.log(this.playerHealth1);
    },
    getRandomValue(min, max){
      return Math.floor(Math.random()*(max-min))+min;
    },
    healPlayer(){
      const healValue = this.getRandomValue(9,19);
      this.playerHealth1 += healValue;
      const newLog = {
       type: 'heal',
       message: 'You healed for ' + healValue + ' health'
     }
     this.logs.unshift(newLog);
      if(this.playerHealth1 > 100) this.playerHealth1 = 100;
      this.attackPlayer();
      this.currentRound +=1;
      //console.log(this.playerHealth1)
    },
    specialAttack(){
      const attackValue = this.getRandomValue(10, 25);
      this.monsterHealth1 = this.monsterHealth1 - attackValue;
      const newLog = {
            type: 'specialAttack',
            message: 'You attecked for ' + attackValue + ' damage'
          }
          this.logs.unshift(newLog);
     if(this.monsterHealth1 < 0) this.monsterHealth1 = 0;
     this.currentRound +=1;
     //console.log(this.monsterHealth1);
      this.attackPlayer();
    },
    loseGame(){
      this.playerHealth1 = 0;
    },
    resetGame(){
      this.playerHealth1 = 100;
      this.monsterHealth1 = 100;
      this.currentRound = 0;
      this.logs = [];
    }
  }
}
</script>

<style>

</style>
