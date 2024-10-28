<script setup>
import { ref, defineProps} from 'vue';

const props = defineProps(['updateMode']);
const valSetting = ref(false);
const valLevel = ref(false);
const valMode = ref(false);
// const wordNumber = ref(100);
const emits = defineEmits(['number']);
// emits('number', wordNumber.value)
const refreshPage = () => {
  window.location.reload();
};
const showSetting = () => {
  valSetting.value = !valSetting.value;
  if (valSetting.value === true) {
    document.getElementById("setting").style.display = "block";
    return
  } else {
    document.getElementById("setting").style.display = "none";
    return
  }
};

const changeNuit = () => {
    props.updateMode('nuit')
};
const changeJour = () => {
    props.updateMode('jour')
};


const showLevel = () => {

valLevel.value = !valLevel.value;
if (valLevel.value === true) {
    document.getElementById("niveau").style.display = "block";
    document.getElementById("niveau").style.display = "flex";
    document.querySelectorAll(".ouvre")[1].style.color = "red"
    document.getElementById("niveau").style.flexDirection = "column";
    return
} else {
    document.getElementById("niveau").style.display = "none";
    document.querySelectorAll(".ouvre")[1].style.color = "black"
    return
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

function choosePhrase(words){
  emits('number', words);
};

function chooseLevel(word) {
  if (word === 50) {
    alert("FACILE");
    choosePhrase(50);
    showLevel();
    showSetting();
    return
  } else if (word === 150){
    alert("NORMALE");
    choosePhrase(150);
    showLevel();
    showSetting();
    return
  } else if (word === 250) {
    
    alert("DIFFICILE")
    choosePhrase(250);
    showLevel();
    showSetting();
    return
    // wordNumber.value = 250;
} else {
    return
}
}
</script>

<template>
  <nav>
    <span><img src="../assets/svg/skillSprinttt.jpg" alt="LOGO" class="logo"></span>
    <ul>
      <li>
        <RouterLink to="/">
          <img src="../assets/svg/home_24dp_75FB4C_FILL0_wght400_GRAD0_opsz24.svg" alt="Home" />
        </RouterLink>
      </li>
      <li @click="refreshPage"> <!-- Ajout de l'événement click -->
        <img src="../assets/svg/refresh_24dp_75FB4C_FILL0_wght400_GRAD0_opsz24.svg" alt="Refresh" />
      </li>
      <li>
        <img src="../assets/svg/play_circle_24dp_75FB4C_FILL0_wght400_GRAD0_opsz24.svg" alt="Play" />
      </li>
      <li @click="showSetting">
          <img src="../assets/svg/settings_24dp_75FB4C_FILL0_wght400_GRAD0_opsz24.svg" alt="Setting" />
      </li>
    </ul>
  </nav>

  <div id="setting">
        <button @click="showMode" class="setBout ouvre">Mode</button> <br>
        <div id="mode">
            <button @click="changeNuit">Nuit</button>
            <button @click="changeJour">Jour</button>
        </div>
        <button @click="showLevel" class="setBout ouvre">Niveau</button> <br>
        <div id="niveau">
            <button @click="chooseLevel(50)">Facile</button>
            <button @click="chooseLevel(150)">Normale</button>
            <button @click="chooseLevel(250) ">Difficile</button>
        </div>
        <!-- <RouterLink to="/sprint"><button class="setBout ouvre">Quitter</button></RouterLink> -->
    </div>
</template>

<style scoped>
nav {
  background-color: #b7beba; 
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);  
  padding: 10px 20px; 
  border-radius: 8px; 
  position: relative; 
  z-index: 1000; 
  display: flex;
  text-align: center;
  justify-content: space-around;
  font-weight: 800;
  font-size: 25px;
}

ul {
  width: 25%;
  display: flex;
  justify-content: space-between; 
  align-items: center; 
  margin: 0;
  padding: 0;
}

li {
  list-style-type: none;
}

img {
  width: 60px; 
  height: 34px; 
  cursor: pointer; 
  transition: transform 0.2s, filter 0.2s
}

.logo {
  border-radius: 30px;
  border: 2px dashed orange;
  width: 100px;
  box-shadow: 1px 1px 1px 1px rgba(12, 12, 12, 0.205);
  position: relative;
  animation-name: example;
  animation-duration: 4s;
  animation-iteration-count: infinite;
  animation-timing-function: linear;
}

@keyframes example {
  to { left: 0px }
  from { left: 100px }
}

img:hover {
  transform: scale(1.1); 
  filter: drop-shadow(0 0 5px rgba(0, 0, 0, 0.2)); 
}

li + li {
  margin-left: 20px; 
}

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
#setting {
  display: none;
  background-color: rgba(134, 204, 94, 0.733);
  width: 20%;
  border-radius: 10px;
  margin: 0 auto;
  position: relative;
  left: 36%;
}
</style>