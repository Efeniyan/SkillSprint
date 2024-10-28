<template>
    <header>
        <nav>
            <span class="moving-image"><img src="../assets/sprint.svg" alt=""></span>

            <ul>
                <ul class="libr">
                    <li>Bibliothèque</li>
                    <router-link to="/scolaire">
                        <li>Edition Scolaire</li>
                    </router-link>
                </ul>
                <ul>
                    <li class="dropdown">
                        Produits
                        <ul class="dropdown-content">
                            <li>SkillSprint</li>
                            <p>Apprends à taper au clavier rapidement et efficacement avec les cours gratuits de
                                TypingClub.</p>
                            <li>Vocabulaire et Orthographe</li>
                            <p>Deviens incollable sur la grammaire et les mots les plus fréquents pour renforcer tes
                                compétences en vocabulaire et en orthographe.</p>
                            <li>Citoyenneté Numérique</li>
                            <p>Acquiers les compétences essentielles en matière de citoyenneté numérique et d'éducation
                                numérique grâce à nos cours ludiques.</p>
                            <li>Apprentissage Emotionnel et Social</li>
                            <p>Apprends les compétences sociales et émotionnelles nécessaires à travers cinq séquences
                                ludiques : conscience de soi, auto-régulation, conscience sociale, les compétences
                                relationnelles et prise de décicions responsable.</p>
                        </ul>
                    </li>
                </ul>
                <span class="english">
                    <li><img src="../assets/traduction.svg" alt=""></li>
                    <ul>
                        <li class="drop" id="languageDropdown" @click="toggleDropdown"> {{ currentLanguage }}
                            <ul class="drop-content" v-if="dropdownVisible">
                                <li @click="changeLanguage('Français')">Français</li>
                                <li @click="changeLanguage('Chinois')">Chinois</li>
                                <li @click="changeLanguage('Portugais')">Portugais</li>
                                <li @click="changeLanguage('Arabe')">Arabe</li>
                                <li @click="changeLanguage('Swahili')">Swahili</li>
                                <li @click="changeLanguage('Allemand')">Allemand</li>
                                <li @click="changeLanguage('Espagnol')">Espagnol</li>
                                <li @click="changeLanguage('Italien')">Italien</li>
                                <li @click="changeLanguage('Polonais')">Polonais</li>
                                <li @click="changeLanguage('Magyar')">Hongrois</li>
                            </ul>
                        </li>
                    </ul>
                </span>
                <div class="link">
                    <router-link to="/login"><button class="nav-button"> Log in</button></router-link>

                    <router-link to="/sign"><button class="nav-button">Sign p</button></router-link>
                </div>
            </ul>
        </nav>

    </header>
    <main>
        <div class="containe">

            <div class="visitez">
                <div class="ok">
                    <h1>Apprenez, enseignez, créez!</h1>
                    <p>Des cours de la plus haute qualité sur la meilleure des plateformes d'apprentissage.</p>
                </div>
                <!-- <router-link to="/home"><button>Visitez-nous</button></router-link> -->

                <img src="../assets/imagee.svg" alt="">
            </div>


        </div>
    </main>
    <footer>
        <div>
            <ul>
                <li><strong>Apprentissage efficace</strong></li>
                <p>
                    Nos cours sont le moyens le plus efficace d'apprendre. Explorez notre bibliothèque de cours.
                    Choisissez votre matière préférée et commencez.
                </p>
            </ul>
        </div>
        <div>
            <ul>
                <li><strong>Enseignement Efficace</strong></li>
                <p>Le portail enseignant propose des outils précieux pour les enseignants. Créez les cours, choisissez
                    les exercices et suivez les progrès de vos élèves en toute simplicité.</p>
            </ul>
        </div>
        <div>
            <ul>
                <li> <strong>Des possibilités illimitées</strong></li>
                <p>Enseignez n'importe quelle matière avec edclub. Choisissez parmi un vaste catalogue de cours
                    interactifs ou créez votre propre contenu.</p>
            </ul>
        </div>
    </footer>

</template>

<script setup>
import { ref } from 'vue';

const currentLanguage = ref('English');
const dropdownVisible = ref(false);

function changeLanguage(language) {
    currentLanguage.value = language;
    dropdownVisible.value = false; // Ferme le dropdown après la sélection
}

function toggleDropdown() {
    dropdownVisible.value = !dropdownVisible.value; // Alterne la visibilité du dropdown
}
</script>


<style scoped>
header {
    border-bottom: solid 1px black;
}

.link {
    display: flex;
    /* Utilise Flexbox pour disposer les boutons */
    gap: 5px;
}

.nav-button {
    border-radius: 8px;
    /* Modifie la valeur selon tes préférences */
    margin-right: 10px;
    /* Espace entre les boutons */
    padding: 8px 16px;
    /* Ajuste le padding si nécessaire */
    border: none;
    /* Enlève la bordure par défaut */
    background-color: #007bff;
    /* Couleur de fond des boutons */
    color: white;
    /* Couleur du texte */
    cursor: pointer;
    /* Change le curseur au survol */
}

.nav-button:last-child {
    margin-right: 0;
    /* Pas d'espace après le dernier bouton */
}

nav {
    border-bottom: 1px solid black;
    margin-top: 20px;
    padding-bottom: 20px;
    font-family: monospace;
}

nav ul {
    display: flex;
    /* Utilise flexbox pour l'alignement */
    padding: 0;
    /* Enlève le padding par défaut */
    margin: 0;
    /* Enlève la marge par défaut */
    list-style-type: none;
    /* Enlève les puces */
}

nav li {
    margin-right: 20px;
}

nav li:last-child {
    margin-right: 0;
}

.english {
    display: flex;
    padding-left: 50%;
    justify-content: space-between;
    margin-right: 10px;
}



main {
    /* background-image: url("../assets/imagee.svg"); 
    background-repeat: no-repeat;
     Pas de répétition de l'image 
    background-size: contain;
    /* L'image est redimensionnée pour être entièrement visible 
    background-position: right center;
    /* Centre l'image dans l'élément 
    padding: 20px;
    /* Ajout de padding pour le contenu 
    color: white;
    /* Couleur de texte pour assurer la lisibilité 
    min-height: 400px;
    /* Assure un minimum de hauteur pour le main */
    background-color: #fff;
    /* Couleur de fond par défaut si l'image n'est pas visible */
    padding-right: 100px;
    width: 95%;
}



img {
    max-width: 100%;
    /* Assure que l'image ne déborde pas */
    height: auto;
    /* Maintient les proportions de l'image */
}

.containe {
    /* Espace entre les éléments */
    align-items: center;
    width: 80%;

    /* Aligne verticalement au centre */
}

.visitez {
    margin-right: 20px;
    width: 100%;
    /* Espace entre la div et la vidéo */
    text-align: center;
    color: black;
    padding: 0 10%;
    padding-top: 80px;
    
    display: flex;
    height: 450px;
    justify-content: space-around;
}
.visitez img{
    padding-left: 50px;
}

.ok{
    padding-top: 150px;
}

main {
    border-bottom: solid 3px #fff;
    padding-bottom: 50px;
    background-color: rgba(245, 243, 240, 255);
}

footer {
    display: flex;
    gap: 30px;
    padding-top: 80px;
}


.moving-image {
    display: inline-block;
    /* Nécessaire pour appliquer l'animation */
    animation: move 5s linear infinite;
    /* Animation de 5 secondes, linéaire et infinie */
}

@keyframes move {
    0% {
        transform: translateX(0);
        /* Position de départ */
    }

    50% {
        transform: translateX(250px);
        /* Déplace l'image de 100 pixels vers la droite */
    }

    100% {
        transform: translateX(0);
        /* Ramène l'image à sa position de départ */
    }
}


.dropdown {
    position: relative;
    display: inline-block;
}

.dropdown-content {
    display: none;
    position: absolute;
    background-color: #f9f9f9;
    min-width: 160px;
    box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
    z-index: 1;
    border-radius: 5px;
}

.dropdown-content li {
    padding: 12px 16px;
    cursor: pointer;
    color: #333;
    transition: background-color 0.3s;
}

.dropdown-content li:hover {
    background-color: #f1f1f1;
}

.dropdown:hover .dropdown-content {
    display: block;
}

/* Style de base pour le menu */
ul {
    list-style-type: none;
    padding: 0;
    margin: 0;
    font-family: Arial, sans-serif;
}

/* Style pour les éléments du menu */
.dropdown {
    position: relative;
    display: inline-block;
    padding: 10px;

    color: black;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s;
}

/* Style pour les paragraphes dans le sous-menu */
.dropdown-content p {
    padding: 0 16px 12px;
    margin: 0;
    color: #555;
    font-size: 14px;
}

.libr {
    margin-top: 10px;
}


.drop {
    position: relative;
    display: inline-block;
    cursor: pointer;
}

.drop-content {
    display: none;
    position: absolute;
    background-color: #f9f9f9;
    min-width: 160px;
    box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
    z-index: 1;
}

.drop-content li {
    padding: 12px 16px;
    cursor: pointer;
    color: #333;
    transition: background-color 0.3s;
}

.drop-content li:hover {
    background-color: #f1f1f1;
}

.drop:hover .drop-content {
    display: block;
}

/* Style de base pour le menu */
ul {
    list-style-type: none;
    padding: 0;
    margin: 0;
    font-family: Arial, sans-serif;
}

/* Style pour les éléments du menu */
.drop {
    position: relative;
    display: inline-block;
    padding: 10px;

    color: black;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s;
}

/* Style pour les paragraphes dans le sous-menu */
</style>