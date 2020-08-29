<template>
<div id="app">
    <!--<img alt="Vue logo" src="./assets/logo.png">-->
    <HelloWorld msg="Welcome to Your Vue.js App" />
    <Game />
</div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import Game from './components/Game'
export default {
    name: 'App',
    components: {
        //HelloWorld,
        Game
    }
}
</script>

<style>
#app {
    font-family: 'Russo One', sans-serif;
    font-size: 24px;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #ffffff;
    margin-top: 60px;
}
body {
    background-image: url("https://i.pinimg.com/originals/d5/f8/21/d5f82167cd30977f97c1818061250968.jpg");
    background-attachment: fixed;
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
}
</style>
