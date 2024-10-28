<template>
    <header>
        <div class="text-container">
            <router-link to="/acceuil"><h3>SprintSkill</h3></router-link>
            <h1>Edition Scolaire</h1>
            <p>
                Suivez les progrès de vos élèves, l'attribution des cours et leur apprentissage en un seul et même endroit. La création du compte est rapide et gratuite.
            </p>
            <div class="button">
                <button>Inscrivez-vous gratuitement</button>
            </div>
        </div>
        <div>
            <img src="../assets/school-hero.svg" alt="Image scolaire" class="image">
        </div>
    </header>

    <main>

        <h4>Pourquoi utiliser l'édition scolaire de SprintSkill ?</h4>
        <h1>
            Notre édition scolaire est une plateforme pédagogique performante utilisée aux États-Unis et dans le monde. Explorez une large sélection de cours conçus avec soin en suivant le programme scolaire dans notre section produits edclub :
        </h1>
        <div class="chute">
            <ul>
                <li>SprintSkill</li>
                <li>Vocabulaire et orthographe</li>
                <li>Citoyenneté numérique</li>
                <li>Apprentissage socio-émotionnel</li>
            </ul>
        </div>
    </main>
    

</template>

<script>

</script>

<style scoped>
body {
    background-color: black; /* Fond noir pour le body */
    color: white; /* Couleur du texte en blanc pour contraster avec le fond noir */
    margin: 0; /* Enlève les marges par défaut */
}

header {
    overflow: auto; /* Pour gérer les flottants */
    border-bottom: 1px solid black;
    background-color: black;
}

.text-container {
    float: left; /* Flotte le texte à gauche */
    width: 60%; /* Ajuste la largeur selon tes besoins */
    color: #fff;
    padding-left: 30px;
    margin-top: 100px;
}

.image {
    float: right; /* Flotte l'image à droite */
    width: 35%; /* Ajuste la largeur selon tes besoins */
    margin-left: 20px; /* Espace entre le texte et l'image */
}


.button {
    text-align: center; /* Centre le bouton dans son conteneur */
    margin-top: 20px; /* Espace au-dessus du bouton, ajuste selon tes besoins */
    padding-left:30px ;
}

button {
    border: none; /* Enlève la bordure par défaut */
    background-color: #4CAF50; /* Couleur de fond du bouton */
    color: white; /* Couleur du texte */
    padding: 10px 20px; /* Espacement intérieur */
    font-size: 16px; /* Taille de la police */
    cursor: pointer; /* Change le curseur au survol */
    border-radius: 12px; /* Arrondi des coins */
    transition: background-color 0.3s; /* Transition pour l'effet hover */
}

button:hover {
    background-color: #45a049; /* Couleur au survol */
}
ul{
    list-style: none;
    display: flex;
    justify-content: space-around;
}

li {
    border-left: 4px solid #4CAF50; /* Bordure à gauche */
    padding: 10px 15px; /* Espacement intérieur */
    margin: 5px 0; /* Espacement entre les éléments */
    color: white; /* Couleur du texte (ajuste selon le fond) */
    background-color: black; /* Couleur de fond pour contraster */
}

</style>