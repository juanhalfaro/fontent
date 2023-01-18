<template>
   <login />
</template>

<script>
export default{
    name: 'Index page',
    layout: 'login',
    components:{
        login
    }
}</script>

<script>
    import login from './components/user/login.vue'
</script>

<style scoped></style>