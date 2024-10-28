<script setup>
import { onMounted, ref } from 'vue';
import { useRouter } from 'vue-router';

const router = useRouter();

const user = ref(null)
const userEmail = ref('');
let password1 = "";
let password2 = "";
const password = ref('');
const userExist = ref(false);
const data = ref([]);

async function fetchUser() {
    const resp = await fetch('/data/users.json');
    data.value = await resp.json();
    console.log(data.value);
}


async function connectUser() {
    console.log(user.value);
    user.value = data.value.filter(el => el.email == userEmail.value)
    console.log(user.value);
    if (user.value.length <= 0) {
        /* if(password.value == user.value[0].password) {
            // router.push('/home');
            alert ("mot de passe déjà utiliser");
        } else {
            router.push('/');
        } */
        if (password1 == password2) {
            router.push("/");
        } else {
            alert("les mots de passe ne sont pas conformes");
        }

    } else {
        alert("L'email entrer existe déjà");
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
    <div>
    </div>

    <div class="main-signup-container">

        <div class="signup-container">
            <h2>Sign Up</h2>
            <form>
                <input type="text" placeholder="Username" required>
                <input v-model="emailUsers" type="email" placeholder="Email" required>
                <input v-model="password1" type="password" placeholder="Password" required>
                <input v-model="password2" type="password" placeholder="Confirm Password" required>
                <button type="submit" @click="submit()" @keyup.enter="submit">Créer mon compte</button>
            </form>
            <div class="login-link">
                <p>Already have an account? <RouterLink to="/" @keyup.enter="submit">Login</RouterLink>
                </p>
            </div>
        </div>
        <div> <img src="../assets/sprint.jpg" alt=""></div>
    </div>

</template>


<style scoped>
.main-signup-container {
    margin: 0;
    padding: 0;
    height: 100vh;
    font-family: 'Press Start   font-family: Verdana, Geneva, Tahoma, sans-serif;2P', cursive;
    background-color: #fff;
    display: flex;
    justify-content: center;
    align-items: center;
    overflow: hidden;
}

.signup-container {
    background: 	#87CEFA;
    padding: 40px;
    border-radius: 15px;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.5);
    width: 300px;
    backdrop-filter: blur(15px);
    border: 2px solid rgba(255, 255, 255, 0.2);
}

h2 {
    color: black;
    text-align: center;
    margin-bottom: 30px;
}

input[type="text"],
input[type="password"],
input[type="email"] {
    width: 100%;
    padding: 10px;
    margin: 10px 0;
    border: 2px solid #ffcc00;
    border-radius: 5px;
    background:rgb(255, 255, 255);
    color: black;
    transition: border-color 0.3s;
}

input[type="text"]::placeholder,
input[type="password"]::placeholder,
input[type="email"]::placeholder {
    color: rgba(0, 0, 0, 0.7);
}

input[type="text"]:focus,
input[type="password"]:focus,
input[type="email"]:focus {
    border-color: #ffcc00;
}

button {
    width: 100%;
    padding: 10px;
    border: none;
    border-radius: 5px;
    background-color: #ffcc00;
    color: black;
    cursor: pointer;
    margin-top: 20px;
    font-weight: bold;
    transition: background-color 0.3s;
}

button:hover {
    background-color: #e6b800;
}

.login-link {
    text-align: center;
    margin-top: 15px;
    color: black;
}

.login-link a {
    color: black;
    text-decoration: underline;
}
</style>