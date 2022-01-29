<template>
    <div class="wrap">
        
            <button @click="attack">Attack</button>
            <button @click="specialAttack" :disabled="disable">Special Attack</button>
       
            <button @click='heal'>Heal</button>
            <button @click='surrender'>Surrender</button>
        
    </div>
</template>
<script>
export default {
    name:'SpecialButtons',
    methods:{
        attack(){
            this.$emit('attacked');
        },
        heal(){
            this.$emit('healed');
        },
        specialAttack(){
            this.$emit('special-attacked');
        },
        surrender(){
            this.$emit('surrender');
        }
    },
    props: ['currentRound'],
    computed:{
        disable(){
            return this.currentRound % 3 !== 0;
        }
    }
}
</script>
<style scoped>
button{
    height: 3.5rem;
    background-color: rgba(68, 31, 27, 0.904);
    padding: 0.2rem;
    margin: 2rem;
    width: 30%;
    border-radius: 15px;
    color: white;
    font-weight: bold;
    font-size: 1.3rem;
    font-family: sans-serif;
    border-style: none;
}
.wrap{
   
    display: flex;
    align-items: center;
    justify-content: center;
    flex-wrap: wrap;
    flex-direction: row;
}
button:disabled{
    background-color: #ccc;
    border-color: #ccc;
    box-shadow: none;
    color:#3f3f3f;
    cursor: not-allowed;
}
button:hover{
    background-color: rgba(110, 49, 42, 0.904);
}
</style>