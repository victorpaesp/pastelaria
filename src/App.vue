<template>
  <div class="#app"> 
    <Background />
    <Wave />
    <Form />
    
    <Division />
    <!--<input type="text" v-model="itemTeste" @keyup.enter="addItem" class="teste">

    <input type="text" v-model="itemTeste2" @keyup.enter="addItem" class="teste3">-->
    <!--<ul>
    <li v-for="item of itens" :key="item.id" class="teste2"></li></ul>-->
  </div>
</template>

<script>
import Background from './components/atoms/Background.vue';
import Wave from './components/atoms/Wave.vue';
import Form from './components/molecules/Form.vue';

import Division from './components/atoms/Division.vue';
import './assets/styles/global.css';

export default {
  name: 'App',
  /*data() {
    return {
      itens: [],
      itemTeste: '',
      itemTeste2: '',
    }
  },*/
  components: {
    Background,
    Wave,
    Form,
    Division
  }/*,
  async created() {
    try {
      const res = await axios.get(`baseURL`);
      this.itens = res.data; 
    } catch (e) {
      console.error(e);
    }
  },
  methods: {
    async addItem(){
      const res = await axios.post(baseURL, { titulo: this.itemTeste, sabor: this.itemTeste2})
      

      this.itens = [...this.itens, res.data]
      

      this.itemTeste = '';
      
      this.itemTeste2 = '';
    }
  }*/
}
</script>

<style>
.app {
    background: transparent radial-gradient(closest-side at 50% 50%, #FFFFFF 0%, #FFFFFF 67%, #FFFFFF00 100%) 0% 0% no-repeat padding-box;
    opacity: 1;
}

html { 
  background-color: #FFFFFF; 
} 

body {
    top: 2px;
    left: 8px;
    width: 1920px;
    height: 1233px;
    background: transparent url('./assets/img/patterns/pattern-1.png') 0% 0% padding-box;
    position: relative;
}


/*
.teste {
  background-color: red;
  width: 200px;
  height: 200px;
  position: absolute;
}


.teste3 {
  background-color: blue;
  width: 200px;
  height: 200px;
  position: absolute;
  left: 200px;
}

.teste2 {
  background-color: blue;
  width: 200px;
  height: 200px;
  position: absolute;
  left: 0;
}*/
</style>
