<template>
  <div class="#app"> 
    <Gradient />
    <Images />
    <Formulario />    
    <Division />
    <Card />
    <Card />
  </div>
</template>

<script>
import Gradient from './components/atoms/Gradient.vue';
import Images from './components/molecules/Images.vue';
import Formulario from './components/molecules/Formulario.vue';
import Division from './components/atoms/Division.vue';
import Card from './components/molecules/Card.vue';
import './assets/styles/global.css';

export default {
  name: 'App',
  components: {
    Gradient,
    Images,
    Formulario,
    Division,
    Card
  }
}
</script>

<style>
html { 
  background-color: #FFFFFF; 
  overflow-x: hidden;
} 

body {
    position: relative;
    top: 2px;
    left: 0;
    width: 1920px;
    height: 1233px;
    background: transparent url('./assets/img/patterns/pattern-1.png') 0% 0% padding-box;
}

</style>
