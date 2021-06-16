<template>
    <div class="text-center text-green-900 mt-4 text-4xl p-6 font-bold">
        Login
    </div>

    <div class="text-center">
        <!-- <input required autofocus v-model="name" class="text-lg text-green-800 mx-5 p-2 my-4 md:my-6 border rounded border-green-700 w-2/3 bg-green-100 focus:outline-none focus:border-green-900" type="text" placeholder="Enter Name"> -->
        <input required v-model="email" class="text-lg text-green-800 mx-5 p-2 my-4 md:my-6 border rounded border-green-700 w-2/3 bg-green-100 focus:outline-none focus:border-green-900" type="email" placeholder="Enter Email">
        <input required v-model="password" class="text-lg text-green-800 mx-5 p-2 my-4 md:my-6 border rounded border-green-700 w-2/3 bg-green-100 focus:outline-none focus:border-green-900" type="password" placeholder="Enter Password">
        <br>
        <button v-on:click="login" class=" mb-3 text-white bg-green-700 rounded p-2 text-lg mt-3 hover:bg-green-900">Login</button>
        <div class="p-1 text-gray-500">
            Don't have an account, 
            <router-link class="underline text-green-700 font-bold" to="/sign-up"> Sign Up</router-link>
        </div>
    </div>
    
</template>

<script>
import axios from 'axios'
export default {
    name: 'Login',
    data(){
        return{
            email:'',
            password:''
        }
    },
    methods: {
        async login(){
            let result = await axios.get(`http://localhost:3000/users?email=${this.email}&password=${this.password}`);
            
            if(result.status == 200 && result.data.length > 0){
                localStorage.setItem("user-info", JSON.stringify(result.data[0]));
                this.$router.push({name: 'Home'});
            }
        }
    },
    mounted(){
        let user = localStorage.getItem("user-info");
        if(user){
            this.$router.push({name: 'Home'});
        }
    }
}
</script>