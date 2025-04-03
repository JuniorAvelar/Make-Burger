<template>
    <div id="nav">
        <router-link to="/" id="img-logo">
            <img :src="logo" :alt="alt" id="logo">
        </router-link> |
        
        <router-link to="/">Home</router-link> 
        <router-link to="/Pedidos">Pedidos</router-link>
    </div>
</template>

<script>    
    export default {
        name: 'NavBar',
        props: ['logo' , 'alt'] 
    }
</script>

<style scoped>
    #nav {
        background-color: #222;
        border-bottom: 4px solid #111;
        padding:  15px 50px;
        display: flex;
        justify-content: flex-end;
    }

    #nav #img-logo {
        margin: auto;
        margin-left: 0;
    }

    #logo {
        height: 40px;
        width:40px
    }

    #nav a {
        color: #fcba03;
        text-decoration: none;
        margin: 12px;
        transition: 0.5s;
    }

    #nav a:hover {
        color:#fff
    }

</style>