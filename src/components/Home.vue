<template>
    <Header />
    <div class="text-center text-green-900 mt-4 text-4xl p-6 font-bold">
        <span class="text-green-700 text-3xl">
            Hi
        </span>
        {{Name}}
    </div>
    
</template>

<script>
import Header from './Header'
export default {
    name: 'Home',
    components: {
        Header
    },
    data(){
        return{
            Name:''
        }
    },
    mounted(){
        let user = localStorage.getItem("user-info");
        if(!user){
            this.$router.push({name: 'SignUp'});
        }else{
            user = JSON.parse(user);
            console.log(user.name);
            this.Name = user.name;
        }
    }
}
</script>