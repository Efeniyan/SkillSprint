<script setup>
import Login from './Login.vue';
import Charger from './Charger.vue';
import { onMounted } from 'vue';

function affichage() {
    const elem = document.querySelectorAll(".login");
    elem[1].style.display = "none"
    setTimeout(() =>{
    elem[0].style.display = "none"
    elem[1].style.display = "block"

},1000)
    
}

onMounted(() => {
    affichage();
})
</script>


<template>
<div class="login">
    <Charger></Charger>
</div>
<div class="login">
    <Login></Login>
</div>


</template>


<style scoped>

</style>