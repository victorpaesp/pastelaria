<template>
  <div class="#app">
      <Gradient />
      <Images />
      <Formulario />    
      <Division />
  </div>
</template>

<script>
import Gradient from './components/atoms/Gradient.vue';
import Images from './components/molecules/Images.vue';
import Formulario from './components/molecules/Formulario.vue';
import Division from './components/atoms/Division.vue';
import './assets/styles/global.css';

export default {
  name: 'App',
  components: {
    Gradient,
    Images,
    Formulario,
    Division
  }
}
</script>

<style>
html {
  background-color: #FFF;
}

body {
    position: relative;
    top: 0px;
    left: 8px;
    width: 1920px;
    background: transparent url('./assets/img/patterns/pattern-1.png') 0% 0% padding-box;
}

</style>