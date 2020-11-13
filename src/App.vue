<template>
    <div id="nav">
        <router-link :to="{ name: 'EventList' }">Events</router-link> |
        <router-link :to="{ name: 'About' }">About</router-link>
    </div>
    <img alt="Vue logo" src="./assets/logo.png" />
    <router-view />
</template>

<style>

    body {
        display: flex;
        flex-direction: column;
        align-items: center;
        background-color: #eeeded;
    }

    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        max-width: 1440px;
        width: 100%;
    }

    #nav {
        padding: 30px;
    }

    #nav a {
        font-weight: bold;
        color: #2c3e50;
    }

    #nav a.router-link-exact-active {
        color: #42b983;
    }

    h4 {
        margin: 10px 0;
    }
</style>
