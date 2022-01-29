<template>
    <div>
        <h2>Battle Log</h2>
        <ul v-for="log in logs" :key="log.message">
            <li :class="defineStyle(log)">{{log.message}}</li>
        </ul>
    </div>   
</template>
<script>
export default {
    name: 'BattleLog',
    props: ['logs'],
    methods:{
        defineStyle(log){
            if(log.type === 'playerAttack') return 'log--player';
            else if(log.type === 'monsterAttack') return 'log--monster';
            else if(log.type === 'specialAttack') return 'log--damage';
            else return 'log--heal';
        }
    }
}
</script>
<style scoped>
div{
    
    width: 80%;
    box-shadow: 0 2px 8px rgb(102, 102, 102);
    text-align: center;
    align-content: center;
    margin-left: 10%;
    margin-bottom: 2rem;
    margin-top: 2rem;
    border-radius: 10px;
}
h2{
    font-weight: bold;
    font-size: 2rem;
    padding-top: 1rem;
}
.log--player{
    color: #7700ff;
}
.log--monster{
    color: #da8d00;
}
.log--damage{
    color: red;
}
.log--heal{
    color: green;
}
ul{
    list-style-type: none;
    margin-right: 3rem;
}
</style>