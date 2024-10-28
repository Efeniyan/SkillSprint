<script setup>
import { ref, onMounted } from 'vue';
import Header from '@/components/Header.vue';

const RecapView = ref(false);
const score = ref(15); // Déclaration de score
const speed = ref(12);
const duration = ref(60);
const coleur = ref(false);
const starCompleted = ref(null);


function animateText(element, text, delay) {
  element.innerHTML = ""; // Vider l'élément
  const letters = text.split("");

  letters.forEach((letter, index) => {
    setTimeout(() => {
      element.innerHTML += letter; // Ajouter la lettre
      element.style.opacity = 1; // Rendre le texte visible
    }, index * delay); // Délai entre chaque lettre
  });
}

function startAnimation() {
  const titleText = "Bienvenue au Skill Sprint!"; // Déclaration
  const paragraphText = "Améliorez votre dactylographie en vous amusant!"; // Déclaration
  const h2Text = "Prêt à commencer?"; // Déclaration
  const titleElement = document.getElementById("animation-title");
  const paragraphElement = document.getElementById("animation-paragraph");
  const h2Element = document.getElementById("animation-h2");
  const startButton = document.getElementById("start-button");

  startButton.style.display = "block";

  animateText(titleElement, titleText, 30); // 30 ms pour le titre

  setTimeout(() => {
    animateText(paragraphElement, paragraphText, 70); // 70 ms pour le paragraphe
  }, titleText.length * 30);

  setTimeout(() => {
    animateText(h2Element, h2Text, 70); // 70 ms pour le h2
  }, (titleText.length + paragraphText.length) * 30 + 30);
}

onMounted(() => {
  startAnimation(); // Démarrer l'animation après le montage
});




</script>

<template>
  <!-- Déconnection -->

  <div class="ntb">
    <Header></Header>
  </div>





  <!-- ********************* -->
  <div class="home1"></div>
  <div class="home2">
    <div class="home">
      <header>
        <h1 id="animation-title">Bienvenue au Skill Sprint!</h1>
        <p id="animation-paragraph">Améliorez votre dactylographie en vous amusant!</p>
      </header>

      <section class="cta">
        <h2 id="animation-h2">Prêt à commencer?</h2>
        <div class="aligne">
          <button class="btn" id="start-button" ><router-link
              to="/sprint">Start</router-link></button>
        </div>
      </section>
    </div>
  </div>


  <!-- /*********************recap**************************** / -->
  <div class="Rcp">
    <div class="recap" v-if="RecapView">
      <div class="sommaire">
        <h2>Récapitulatif de votre frappe</h2>

        <div id="stars">
          <span v-for="i in 5" :class="{ star: coleur }"><svg
              :fill="(starCompleted !== null && starCompleted >= i) ? 'yellow' : '#000000'" width="50px" height="50px"
              viewBox="0 0 256 256" id="Flat" xmlns="http://www.w3.org/2000/svg">
              <g opacity="0.2">
                <path
                  d="M132.41106,190.73266l50.43543,31.95385c6.44693,4.08451,14.45124-1.99032,12.53819-9.51579l-14.57192-57.32241a8.75742,8.75742,0,0,1,2.83756-8.87589l45.2273-37.64345c5.94268-4.9462,2.87542-14.80876-4.75965-15.30428l-59.06388-3.83326a8.41836,8.41836,0,0,1-7.24792-5.3506l-22.02834-55.473a8.31887,8.31887,0,0,0-15.55566,0L98.19383,84.84083a8.41836,8.41836,0,0,1-7.24792,5.3506L31.882,94.02469c-7.63507.49552-10.70233,10.35808-4.75965,15.30428l45.2273,37.64345a8.75742,8.75742,0,0,1,2.83756,8.87589L61.6734,209.00846c-2.29566,9.03056,7.30952,16.32036,15.04583,11.41895l46.86971-29.69475A8.21431,8.21431,0,0,1,132.41106,190.73266Z" />
              </g>
              <path
                d="M187.2627,231.9834a16.22513,16.22513,0,0,1-8.69825-2.53931l-50.43457-31.95361v.00024a.21827.21827,0,0,0-.25976,0L81,227.1853a17.80084,17.80084,0,0,1-20.08008-.63134,18.36991,18.36991,0,0,1-6.999-19.51661l13.51367-53.16a.77184.77184,0,0,0-.20215-.75562L22.00391,115.47791a16.65647,16.65647,0,0,1-5.16407-18.06019A16.36086,16.36086,0,0,1,31.36328,86.0415l59.06445-3.83325a.45615.45615,0,0,0,.33008-.31885l22.0293-55.47424a16.31782,16.31782,0,0,1,30.42578.00037l22.0293,55.47265a.45648.45648,0,0,0,.3291.32007l59.06543,3.83313a16.36115,16.36115,0,0,1,14.52344,11.37634,16.656,16.656,0,0,1-5.16407,18.05994l-45.22754,37.64356a.76927.76927,0,0,0-.20214.75659l14.57129,57.3219a16.6353,16.6353,0,0,1-6.3418,17.67138A16.21482,16.21482,0,0,1,187.2627,231.9834ZM128,181.46558a16.23665,16.23665,0,0,1,8.69238,2.509v.00024l50.43555,31.95386a.579.579,0,0,0,.14551.07373.818.818,0,0,0,.30566-.2666.646.646,0,0,0,.05274-.59424l-14.57227-57.32226a16.812,16.812,0,0,1,5.47363-16.99622l45.22657-37.64294a.64454.64454,0,0,0,.18652-.81043c-.11328-.3468-.23145-.35449-.34668-.36194l-59.06445-3.83325a16.4984,16.4984,0,0,1-14.16407-10.38232L128.3418,32.32043C128.21484,32,128.13379,32,128,32s-.21484,0-.3418.32007L105.62891,87.79346a16.49935,16.49935,0,0,1-14.165,10.3811l-59.06348,3.83325c-.11523.00745-.2334.01514-.34668.36194a.64479.64479,0,0,0,.18652.81055l45.22754,37.64331a16.81409,16.81409,0,0,1,5.47364,16.99512L69.42676,210.97949a2.334,2.334,0,0,0,.88672,2.62232,1.71518,1.71518,0,0,0,2.123.06811l46.8711-29.69507A16.23481,16.23481,0,0,1,128,181.46558Z" />
            </svg></span>
        </div>
      </div>

      <div class="summary-container">
        <div class="circle">
          <div class="circle-content">
            <p><strong>{{ speed }} MPM</strong></p>
          </div>
          <p class="dure">Vitesse</p>
        </div>

        <div class="circle duration-circle">
          <div class="circle-content">
            <p><strong>{{ duration }} s</strong></p>
          </div>
          <p class="dure">Durée</p>
        </div>
      </div>
      <div class="btnR">
        <router-link to="/"><button><img src="../assets/repeate.svg" alt=""></button></router-link>
      </div>
    </div>
  </div>
</template>




<style scoped>
/******************************** /

/  ********************************** */

html,
body {
  height: 100%;
  margin: 0;
  overflow: hidden;
}

#animation-title,
#animation-paragraph,
#animation-h2 {
  display: inline-block;
  font-size: 2em;
  opacity: 0;
  transition: opacity 0.5s ease;
}
a{
  text-decoration: none;
  color: black;
  font-size: 18px;
}



.home2 {
   /* position: fixed;  */
  background: transparent;
  backdrop-filter: blur(2px);
  text-align: center;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  height: 100vh;
  
}

.home1 {
  position: fixed;
  width: 100%;
  height: 100%;
  background-image: url('../assets/Work.gif');
   /* background-color: #87CEFA;  */
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;

  z-index: -10;
}

.home {
  z-index: 50;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  padding: 20px;
  margin: 0 auto;
  /* background-color:rgba(189, 194, 194, 0.363) ;  */
  height: 100vh;
}

header {
  color: black;
  padding: 20px;
  flex: 1;
  margin-top: 200px
}

.cta {
  margin-bottom: 300px;
  flex: 1;
  text-align: center;
}

h1,
h2,
p {
  width: 100%;
  margin: 10px 0;
}

h1 {
  font-size: 2.5em;
}

h2 {
  font-size: 2em;
  color: black;
  padding-bottom: 20px;
}

p {
  font-size: 1.2em;
}


.aligne {
  /* text-align: center;  */
  margin-top: 20px;
  padding-left: 50px;
}



/* .ntb {
  position: fixed;
  top: 20px;
  right: 20px;
  z-index: 1000;
} */

/* .deconnecte {
  background-color: #ff4d4d;
  color: white;
  border: none;
  border-radius: 5px;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
  transition: background-color 0.3s ease;
} */

.btn {
  display: inline-block;
  padding: 10px 10px;
  background-color: rgb(48, 212, 76);
  color: white;
  text-decoration: none;
  border-radius: 5px;
  transition: background-color 0.3s;
  width: 70%;
  max-width: 300px;
  text-align: center;
  margin-right: 60px;
  font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
}

.deconnecte:hover {
  background-color: #ff1a1a;
}
</style>