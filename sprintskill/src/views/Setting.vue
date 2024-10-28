<script setup>
import { ref } from 'vue';

const wordNumber = ref(null);
const valLevel = ref(false);
const valMode = ref(false);
const showLevel = () => {

    valLevel.value = !valLevel.value;
    if (valLevel.value === true) {
        document.getElementById("niveau").style.display = "block";
        document.getElementById("niveau").style.display = "flex";
        document.querySelectorAll(".ouvre")[1].style.color = "red"
        document.getElementById("niveau").style.flexDirection = "column";
    } else {
        document.getElementById("niveau").style.display = "none";
        document.querySelectorAll(".ouvre")[1].style.color = "black"
    }
};
const showMode = () => {

    valMode.value = !valMode.value;
    if (valMode.value === true) {
        document.getElementById("mode").style.display = "block";
        document.querySelectorAll(".ouvre")[0].style.color = "red"
        document.getElementById("mode").style.display = "flex";
        document.getElementById("mode").style.flexDirection = "column";
    } else {
        document.getElementById("mode").style.display = "none";
        document.querySelectorAll(".ouvre")[0].style.color = "black"
    }
};

function chooseLevel(level) {
    if (level === 50) {
        alert("FACILE");
        wordNumber.value = 50;
        return
    } else if (level === 150){
        alert("NORMALE")
        wordNumber.value = 150;
    } else if (level === 250) {

        alert("DIFFICILE")
        wordNumber.value = 250;
    } else {
        return
    }
}

</script>


<template>

    <button @click="showMode" class="setBout ouvre">Mode</button> <br>
    <div id="mode">
        <button>Nuit</button>
        <button>Jour</button>
    </div>
    <button @click="showLevel" class="setBout ouvre">Niveau</button> <br>
    <div id="niveau">
        <button @click="chooseLevel(50)">Facile</button>
        <button @click="chooseLevel(150)">Normale</button>
        <button @click="chooseLevel(250) ">Difficile</button>
    </div>
    <RouterLink to="/sprint"><button class="setBout ouvre">Quitter</button></RouterLink>


</template>


<style scoped>
#niveau {
    display: flex;
    flex-direction: column;
    gap: 5px;
    margin: 5px;
    display: none;
}
#mode {
    display: flex;
    flex-direction: column;
    gap: 5px;
    margin: 5px;
    display: none;
}
.setBout{
    border: none;
    margin: 3px;
    background-color: rgba(255, 255, 255, 0);
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    font-size: 20px;
}
</style>