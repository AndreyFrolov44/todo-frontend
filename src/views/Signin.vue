<template>
    <div>
        <form @submit="login">
            <label for="username">Введите логин</label>
            <input v-model="username" type="text" id="username" placeholder="Логин...">
            <label for="password">Введите пароль</label>
            <input v-model="password" type="text" id="password" placeholder="Пароль...">
            <button type="submit">Войти</button>
        </form>
    </div>
</template>

<script>
export default {
    name: 'Signin',
    data(){
        return{
            username: "",
            password: ""
        };
    },
    methods: {
        login(event){
            event.preventDefault();

            this.axios
                .post('http://127.0.0.1:8000/api/auth/token/login/', {username: this.username, password: this.password})
                .then(response => {this.setLogined(response.data.auth_token)})
                .catch(err => {console.error(err)})
        },
        setLogined(token){
            console.log(token);
        }
    }
}
</script>



