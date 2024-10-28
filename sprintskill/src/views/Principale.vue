<script setup>
import acceuil from './Acceuil.vue';
import Charger from './Charger.vue';
import { onMounted } from 'vue';

function affichage() {
    const elem = document.querySelectorAll(".acceuil");
    elem[1].style.display = "none"
    setTimeout(() =>{
    elem[0].style.display = "none"
    elem[1].style.display = "block"

},5000)
    
}

onMounted(() => {
    affichage();
})
</script>


<template>
<div class="acceuil">
    <Charger></Charger>
</div>
<div class="acceuil">
    <acceuil></acceuil>
</div>


</template>


<style scoped>

</style>