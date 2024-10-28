<script setup>
import { onMounted, ref } from 'vue'
import { useRouter } from 'vue-router'
import { setAuthentication } from '@/router';

const router = useRouter();

const user = ref(null)
const userEmail = ref('');
const password = ref('');
const userExist = ref(false);
const data = ref([]);

async function fetchUser() {
    const resp = await fetch('/data/users.json');
    data.value = await resp.json();
    //   console.log(data.value);
};

 function connectUser() {
    console.log(user.value);
    user.value = data.value.filter(el => el.email == userEmail.value)
    console.log(user.value)
    if (user.value.length > 0) {
        if (password.value == user.value[0].password) {
            // setAuthentication(true); 
            router.push('/home');
            // alert ("correcte")
        } else {
            alert("mots de passe incorrecte")

        }
    } else {
        // router.push('/login');
        alert("e-mail invalide");
        let roro = prompt("voulez vous avoir un compte? (O/N) ").toUpperCase();
        if (roro === "O") {
            router.push('/sign')
        } else {
            alert("vous n'avez pas de compte")
        }

    }


}

function submit() {
    // console.log(userEmail.value);
    // router.push('/dashboard');
    connectUser();
}

onMounted(() => {
    fetchUser();
})

</script>


<template>
    <div class="main-container">
        <div class="imge"><img src="../assets/sprint.jpg" alt=""></div>
        <div class="login-container">
            <h2>Connexion</h2>
            <form @submit.prevent="submit">
                <input type="email" v-model="userEmail" placeholder="Votre email" required>
                <input type="password" v-model="password" placeholder="Password" required>
                <div class="remember-me">
                    <input type="checkbox" id="remember">
                    <label for="remember">Remember me</label>
                </div>
                <button type="submit" @click="submit()" @keyup.enter="submit"> LOGIN</button>
            </form>
            <div class="forgot-password">
                <a href="#">Mot de passe oublier?</a>
            </div>
            <div class="sign-up">
                <p>Vous êtes nouveau ici? <RouterLink to="/sign" @keyup.enter="submit">S'inscrire</RouterLink>
                </p>
            </div>
        </div>
    </div>

</template>


<style scoped>
/* .imge{
     border: black solid 1px; 
     background-color: #87CEFA; 
} */
.main-container {
    margin: 0;
    padding: 0;
    height: 100vh;
    font-family: Verdana, Geneva, Tahoma, sans-serif;
    background-color: #fff;
    display: flex;
    justify-content: center;
    align-items: center;
}


.login-container {
    background:	#87CEFA;
    padding: 40px;
    border: 15px;
    backdrop-filter: blur(15px);
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.5);
    width: 300px;
    border: 2px solid rgba(255, 255, 255, 0.2);
}

h2 {
    color: black;
    text-align: center;
    margin-bottom: 30px;
    /* text-shadow: 0 0 10px rgba(255, 204, 0, 0.8); */
}

input[type="email"],
input[type="password"] {
    width: 100%;
    padding: 10px;
    margin: 10px 0;
    border: 2px solid #ffcc00;
    border-radius: 5px;
    background: rgba(255, 255, 255, 0.1);
    color: white;
    transition: border-color 0.3s;
}

input[type="email"]::placeholder,
input[type="password"]::placeholder {
    color: rgba(10, 10, 10, 0.7);
}

input[type="email"]:focus,
input[type="password"]:focus {
    border-color: #ffcc00;
}

button {
    width: 100%;
    padding: 10px;
    border: none;
    border-radius: 5px;
    background-color: #ffcc00;
     /* Couleur or  */
    color: black;
    cursor: pointer;
    margin-top: 20px;
    font-weight: bold;
    transition: background-color 0.3s;
}

button:hover {
    background-color: #e6b800;
}

.remember-me {
    color: white;
    margin: 15px 0;
}

.forgot-password,
.sign-up {
    text-align: center;
    margin-top: 15px;
    color: black;
}

.forgot-password a,
.sign-up a {
    color: black;
    text-decoration: underline;
}
</style>