<template>
    <div id="myview">
        <Header @number="wordNumber" :updateMode="updateMode"></Header>
        <div class="typing-club">
            <div class="phrase-container">
                <span class="maClasse" v-for="(elem, index) in newPhrase" :key="index.id">{{ elem }}</span>
            </div>
        </div>
        <div class="progress-bar">
            <div class="progress" :style="{ width: progress + '%' }"></div>
        </div>
        
        <div class="Rcp">
            <div class="recap" v-if="RecapView">
                <div class="sommaire">
                    <h2>Récapitulatif de votre frappe</h2>
                    <div id="stars">
                        <span v-for="i in 5" :class="{ star: coleur }"><svg
                                :fill="(starCompleted !== null && starCompleted >= i) ? 'yellow' : '#000000'" width="50px"
                                height="50px" viewBox="0 0 256 256" id="Flat" xmlns="http://www.w3.org/2000/svg">
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
                            <p><strong>{{ vitesse }} MPM</strong></p>
                        </div>
                        <p class="dure">Vitesse</p>
                    </div>
                    <div class="circle duration-circle">
                        <div class="circle-content">
                            <p><strong>{{ format }} s</strong></p>
                        </div>
                        <p class="dure">Durée</p>
                    </div>
                    <div class="circle duration-circle">
                        <div class="circle-content">
                            <p><strong>{{ precisionTotale }} %</strong></p>
                        </div>
                        <p class="dure">Précision</p>
                    </div>
                </div>
        
                <div class="btnR">
                    <button @click="refreshPage"><img src="../assets/repeate.svg" alt=""></button>
                </div>
            </div>
        </div>
    </div>
</template>


<script setup>

import Header from '@/components/Header.vue';
import { onMounted, ref, computed } from 'vue';

function updateMode(param) {
    if (param === 'nuit') {
        document.getElementById("vieww").style.backgroundColor = "black";
        return
    } else if (param === 'jour') {
        document.getElementById("vieww").style.backgroundColor = "white";
        return
    }
};

const valColor = ref(null);
const defaut = 100;
const wordnumber = ref(null);
let RecapView = ref(false);
let recapTriggered = ref(false);
let coleur = ref(false);
let starCompleted = 0;
let lastKey = ref('');
let phrase = ref([]);
let newPhrase = ref([]);
let g = -1;
let inputText = ref([]);
let totalLength = newPhrase.value.length;
const progress = ref(0);
const precisionTabGreen = ref([]);
const precisionTabOrange = ref([]);
const precisonGreen = ref(null);
const precisonOrange = ref(null);
const precisionTotale = ref(null);
const vitesse = ref(null);
const score = ref(null);
const totalSeconds = ref(null);
const interval = ref(null);
const format = ref("");


function wordNumber(number) {
    // wordnumber.value = number;
    choosePhrase(number);
    console.log(number);
    
}
function startChrono() {
    interval.value = setInterval(() => {
        totalSeconds.value++;
    }, 1000);
};

function refreshPage() {
    window.location.reload();
}


function stopTimer() {
    clearInterval(interval.value);
};


function toggleRecap() {
    RecapView.value = !RecapView.value;
    updateScore(score.value); // Appel de fonction corrigé
}

function updateScore(newScore) {
    score.value = newScore;
    updateStars(newScore); // Appel de fonction corrigé
}

function updateStars(score) {
    if (score >= 1000) {
        starCompleted.value = 5;
    } else if (score >= 800) {
        starCompleted.value = 4;
    } else if (score >= 700) {
        starCompleted.value = 3;
    } else if (score >= 500) {
        starCompleted.value = 2;
    } else if (score >= 200) {
        starCompleted.value = 1;
    } else {
        starCompleted.value = 0; // Valeur par défaut
    }
}


function pressKeyUp(event) {

    format.value = computed(() => {
        const minutes = Math.floor(totalSeconds.value / 60);
        const seconds = totalSeconds.value % 60;

        return `${String(minutes).padStart(2, '0')} : ${String(seconds).padStart(2, '0')}`;
    });
    lastKey.value = event.key;

    const listSpan = document.querySelectorAll(".maClasse")

    inputText.value.push(lastKey.value)
    console.log(inputText.value.length);


    g++;
    for (let i = g; i < newPhrase.value.length; i++) {
        if (inputText.value.length === 1 && listSpan[i].style.backgroundColor !== "brown") {
            startChrono();
        }

        if (g === newPhrase.value.length - 1) {
            if (newPhrase.value[i] === lastKey.value) {
                listSpan[i].style.backgroundColor = "green";

            } else {
                listSpan[i].style.backgroundColor = "red";

            }
            setTimeout(() => {
                ("Vous aviez fini le jeu")
                console.log(listSpan);

                //Fonction de precision

                listSpan.forEach((elem, index) => {
                    if (elem.style.backgroundColor === "green") {
                        precisionTabGreen.value.push(elem)
                    }
                })
                console.log("precisionTabGreen", precisionTabGreen.value);

                precisonGreen.value = Math.floor((precisionTabGreen.value.length / newPhrase.value.length) * 100);
                console.log("precisonGreen", precisonGreen.value);

                listSpan.forEach((elem, index) => {
                    if (elem.style.backgroundColor === "orange") {
                        precisionTabOrange.value.push(elem)
                    }
                })
                console.log("precisionTabOrange", precisionTabOrange.value);
                precisonOrange.value = Math.floor(((precisionTabOrange.value.length / 2) / newPhrase.value.length * 100));
                console.log("precisonOrange", precisonOrange.value);

                precisionTotale.value = precisonGreen.value + precisonOrange.value;

                console.log(" precisionTotale", precisionTotale.value);

                //Fonction de vitesse par mot
                let x = newPhrase.value.join("");
                x = x.split(" ");
                vitesse.value = Math.floor((x.length * 60) / totalSeconds.value);
                console.log(x);
                console.log("vitesse:", vitesse.value);

                //Fonction de score
                score.value = Math.floor((precisionTotale.value * 1000) / 100);
                console.log(score.value);



                stopTimer();

                return



            }, 500)
        } else {

            if (lastKey.value === "Backspace") {
                inputText.value = inputText.value.slice(0, -2);
            }
            progress.value = Math.min((inputText.value.length / newPhrase.value.length) * 100, 100);

            if (lastKey.value === "Backspace") {
                g -= 2;
                listSpan[i - 1].style.backgroundColor = "brown";
                listSpan[i - 1].style.borderBottom = "solid 2px";
                if (listSpan[0] === "") {
                    inputText.value.length = 0;
                }
                return;

            }
            else if (newPhrase.value[i] === lastKey.value) {
                if (listSpan[i].style.backgroundColor === "brown") {
                    console.log(listSpan[i].style.backgroundColor);

                    listSpan[i].style.backgroundColor = "orange";

                    return;
                } else {
                    listSpan[i].style.backgroundColor = "green";
                    listSpan[i].style.borderBottom = "none";
                    listSpan[i + 1].style.borderBottom = "solid 2px";
                    return;
                }
                // console.log(newPhrase.value.length);
                // return;
            } else {
                listSpan[i].style.backgroundColor = "red";
                listSpan[i].style.borderBottom = "none";
                listSpan[i + 1].style.borderBottom = "solid 2px";
                console.log(progress.value);
                return;
            };


        };
    }


    if (inputText.value.length === newPhrase.value.length && !recapTriggered.value) {
        recapTriggered.value = true; // Marquez le récapitulatif comme déclenché
        toggleRecap(); // Déclenchez la fonction de récapitulatif
    }
};

function choosePhrase(level) {
    const tableau = [
       "ainsi la vie continuait rythmee par les saisons et les rencontres chacun trouvait sa place dans ce tableau vivant cultivant des souvenirs precieux et partageant des instants simples mais significatifs le village etait un havre de paix un endroit ou l'on se sentait chez soi entoure de ceux qu'on aimait parfois des voyageurs passaient par le village apportant avec eux des histoires fascinantes et des experiences diverses les villageois les accueillaient chaleureusement curieux d'en apprendre davantage sur leurs aventures ces echanges enrichissaient leur quotidien et leur permettaient de rever a d'autres horizons les habitants se retrouvaient souvent sur la place du village echangeant des nouvelles et partageant des rires ils organisaient des fetes ou la musique resonait et ou chacun pouvait danser sous les etoiles ces moments de convivialite creeaient des liens forts et renforcaient le sens de la communaute au fil des saisons les couleurs changeaient au printemps les arbres fleurissaient offrant un spectacle de teintes vives l'ete apportait la chaleur et les longues journees parfaites pour les pique-niques au bord de la riviere l'automne quant a lui revetait le paysage de nuances dorees tandis que l'hiver couvrait tout d'un manteau blanc scintillant dans un petit village paisible la vie suivait son cours tranquillement les habitants se levaient chaque matin avec le chant des oiseaux et le doux parfum du pain frais qui sortait du four les enfants jouaient dans les ruelles riant et courant sans souci les mamans preparent des plats savoureux utilisant des ingredients locaux comme des tomates juteuses des herbes aromatiques et du fromage frais"];

    // phrase.value = tableau[Math.floor(Math.random() * (tableau.length))];
    const xx = Math.floor(Math.random() * 40);
    phrase.value = tableau[0].substring(xx, level);
    // console.log(phrase.value);
    maPhrase();
};
function maPhrase() {
    newPhrase.value = phrase.value.split("");
    console.log(newPhrase.value);
    return newPhrase.value;
};


// function toggleRecap() {
//     RecapView.value = !RecapView.value;
//     updateScore(500);
//     console.log(RecapView.value);

// };

// function updateScore(newScore) {
//     score = newScore;
//     updateStars(newScore); // Mettre à jour les étoiles
// };

// function updateStars(score) {
//     if (score >= 1000) {
//         // coleur.value = true;
//         starCompleted = 5;
//     } else if (score >= 800) {
//         // star.classList.add('yellow');
//         starCompleted = 4;
//     } else if (score >= 700) {
//         // star.classList.add('yellow');
//         starCompleted = 3;
//     } else if (score >= 500) {
//         // star.classList.add('yellow');
//         starCompleted = 2;
//     } else if (score >= 200) {
//         // star.classList.add('yellow');
//         starCompleted = 1;
//     }

// };




onMounted(() => {
    window.addEventListener('keyup', (event) => pressKeyUp(event));
    choosePhrase(defaut);
    maPhrase();
    // settingShow();

});

</script>

<style scoped>
.typing-club {
    font-family: 'Arial', sans-serif;
    text-align: center;
    background-color: #b7beba;
    padding: 30px;
    border-radius: 12px;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
    transition: background-color 0.3s;

    margin: 10% 20% 1%;
}

.typing-club:hover {
    background-color: #e0e7ee;
}

.phrase-container {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    margin-bottom: 20px;
}

.maClasse {
    font-size: 28px;
    margin: 0 4px;
    transition: transform 0.2s, color 0.3s;
    padding: 4px;
    border-radius: 4px;
}

.maClasse:hover {
    transform: scale(1.1);
    color: #3498db;
}

.progress-bar {
    width: 60%;
    background: #e0e0e0;
    border-radius: 5px;
    overflow: hidden;
    height: 20px;
    margin-top: 20px;
    box-shadow: inset 0 2px 5px rgba(0, 0, 0, 0.1);
    margin: 0 20%;
}

.progress {
    height: 100%;
    background: #4caf50;
    transition: width 0.3s ease-in-out;
}

/*************************************  Css REcapView **********************************************/

.star {
    font-size: 24px;
}

.star.yellow img {
    filter: brightness(1.5);
}

.star-container {
    display: flex;
    justify-content: center;
}

.recap {
    /* background-repeat: no-repeat;
  background-position: center;
  background-size: cover; */

    background-image: url("../assets/cl9.jpg");
    background: transparent;
    background-size: cover;
    backdrop-filter: blur(50px);


    width: 50%;
    margin: auto;

    /*********/
    background-color: #FFFFFF00;
    position: absolute;
    /* top: 0;
  left: 250px; */


    left: 50%;
    top: 40%;
    transform: translate(-50%, -50%);

}

h2 {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.sommaire {
    text-align: center;
    margin: 20px;
}


.circle {
    border: 5px solid;
    width: 150px;
    height: 100px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    color: white;
}

.dure {
    text-align: center;
}

.circle-content {
    font-size: 16px;
    text-align: center;
}

.btnR {
    text-align: center;
    padding: 20px;
}

.summary-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    margin: 20px 0;
    padding-left: 100px;
    gap: 100px;
    width: 75%;
}

button {
    color: red;
    background-color: black;
    font-family: Georgia, 'Times New Roman', Times, serif;
    padding: 20px;
}


@media (max-width: 768px) {
    .circle {
        width: 80px;
        height: 80px;
    }

    .circle-content {
        font-size: 14px;
    }

    .star {
        font-size: 20px;
    }
}

@media (max-width: 480px) {
    .circle {
        width: 60px;
        height: 60px;
    }

    .circle-content {
        font-size: 12px;
    }

    .star {
        font-size: 18px;
    }
}

.Rcp {
    background: #f0f8ff;
    border-radius: 15px;
    padding: 20px;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
    max-width: 400px;
    margin: auto;
    text-align: center;

}

.sommaire h2 {
    color: #333;
    font-family: 'Arial', sans-serif;
}

.star-container {
    margin: 10px 0;
}

.star {
    font-size: 24px;
}

.summary-container {
    display: flex;
    justify-content: space-around;
    margin: 20px 0;
}

.circle {
    background: black;
    border-radius: 50%;
    width: 100px;
    height: 100px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.15);
    transition: transform 0.3s;
}

.circle:hover {
    transform: scale(1.05);
}

.circle-content p {
    margin: 5px 0;
    font-family: 'Arial', sans-serif;
}

.dure {
    color: #9b5b5b;
    font-size: 14px;
}

.btnR {
    margin-top: 20px;
    text-align: center;
}

button {
    border: none;
    border-radius: 5px;
    padding: 10px 20px;
    cursor: pointer;
    font-size: 16px;
    transition: background-color 0.3s;
}

/* button:hover {
} */


.star-container {
    display: flex;
    justify-content: center;
}

.star {
    font-size: 24px;
    margin: 0 2px;
}
</style>