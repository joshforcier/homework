<template>
    <div id="app">
        <Javascript />
        <CSS />
    </div>
</template>

<script>

import Javascript from './components/Javascript.vue';
import CSS from './components/CSS.vue';

export default {
    name: 'app',
    components: {
        Javascript,
        CSS,
    }
}
</script>

<style>
#app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>
