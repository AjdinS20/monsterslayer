<template>
    <div>
        <h1>You lost</h1>
        <p>Press the button to play again</p>
        <button @click="startAgain">Play again</button>
    </div>
</template>
<script>
export default {
    name: 'LostScreen',
    methods:{
        startAgain(){
            this.$emit('start-new');
        }
    }
}
</script>
<style scoped>
div{
    text-align: center;
    font-family:'Times New Roman', Times, serif;
    width: 100%;
    font-size: 5rem;
}
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
</style>