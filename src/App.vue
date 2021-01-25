<template>
  <div id="app">
    <dice></dice>
    <d20></d20>
    <d12/>
    <d100/>
    <d10/>
    <d8/>
    <d6/>
    <d4/>
    <d-custom/>
  </div>
</template>

<script>

import Dice from './components/Dice.vue';
import d20 from './components/d20.vue';
import d6 from './components/d6.vue';
import d12 from './components/d12.vue';
import d100 from './components/d100.vue';
import d10 from './components/d10.vue'
import d8 from './components/d8.vue'
import d4 from './components/d4.vue'
import dCustom from './components/dCustom.vue'

export default {
  name: 'App',
  components: {
    Dice,
    d20,
    d6,
    d12,
    d100,
    d10,
    d8,
    d4,
    dCustom
  }
}
</script>

<style>
body, html, #app {
  font-family: 'Hammersmith One', sans-serif; 
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #12460b; 
  background: 100%, linear-gradient(90deg, rgba(13,0,36,1) 0%, rgba(109,232,45,1) 0%, rgba(0,212,255,1) 97%);
  background-size: auto;
  
  
  
}

</style>
