<template>
    <div class="wraper">
        <h2>Player health</h2>
        <div class="healthbar">
            <div class="healthbar_value" :style="{width: playerHealth1 + '%'}">
            </div>    
        </div> 
    </div>
</template>
<script>
export default {
    name: 'PlayerHealth',
    props:['playerHealth1']
}
</script>
<style scoped>
.wraper{
    height: 7rem;
    width: 80%;
    box-shadow: 0 2px 8px rgb(102, 102, 102);
    text-align: center;
    align-content: center;
    margin-left: 9%;
    margin-bottom: 2rem;
    margin-top: 2rem;
    border-radius: 10px;
    padding-bottom: 1rem;
    padding-left:1rem;
    padding-right: 1rem;
    
}
h2{
    font-weight: bold;
    font-size: 2rem;
    padding-top: 1rem;
}
.healthbar{
    width: 100%;
    height: 40px;
    border: 1px solid #575757;
    margin: 1rem 0;
    background: #fde5e5;
    
}
.healthbar_value{
    background-color: #00a876;
    width: 100%;
    height: 100%;
    
}
</style>