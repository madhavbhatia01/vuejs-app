<template>
    <div class="flex bg-green-700 text-2xl text-white">
        <a href="/" class="p-3 ml-10 w-11/12">
           Home
        </a>
        <div class="hover:bg-green-600 mr-10 p-3">
            <a href="/login" @click="logout">
            Logout
            </a>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Header',
    methods:{
        logout(){
            localStorage.clear();
        }
    }
}
</script>