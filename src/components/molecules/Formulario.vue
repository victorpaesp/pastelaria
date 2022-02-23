<template>
  <div>
    <div class="form">
        <div class="form-header">
            <p class="text-header">Monte aqui o seu cardápio. O que está esperando?</p>
            <p class="switch"> 
                <ToggleButton />
            </p>
        </div>
        
      <form action="." id="form-pastel" v-on:submit="addItem">
        <div class="start-row">
            <Input id="titulo" name="titulo" v-model="titulo" placeholder="Título do Pedido"/>
            <Input id="sabor"  name="sabor"  v-model="sabor"  placeholder="Sabor"/>
            <Input id="preco"  name="preco"  v-model="preco"  placeholder="R$" ref="file"/>
        </div>
        <div class="middle-row">
            <Textarea id="descricao" name="descricao" v-model="descricao" placeholder="Descrição" />
        </div>
        <div class="end-row">
            <InputFile id="imagem" name="imagem" v-model="imagem" /> 
        </div>
      <Button />
      </form>
    </div>
      <table style="background-color: red; position: absolute; left: 500px: top: 500px: width: 500px; height: 500px">
        <tr v-for="item of itens" :key="item.id">
          <td>{{ item.id }}</td>
        </tr>
      </table>
    
        <!-- 
          <button style="height: 100px; width: 100px; position: absolute; top: 515px;" @click="deleteItem()">Delete</button>

          <button style="height: 100px; width: 100px; position: absolute; top: 515px; left:500px" @click="getItem()">Get</button> 
        -->
  </div>
</template>

<script>
import axios from 'axios';
import Button from '@/components/atoms/Button.vue'
import Input from '@/components/atoms/Input.vue';
import Textarea from '@/components/atoms/Textarea.vue';
import InputFile from '@/components/atoms/InputFile.vue';
import itens from '@/services/itens.js'

import ToggleButton from '@/components/atoms/ToggleButton.vue';

const baseURL = "http://localhost:3000/itens";

export default {
    name: 'Formulario',
    data() {
        return {
            itens: [],
            titulo: null,
            sabor: null,
            preco: null,
            descricao: null,
            imagem: null,
        }
    },
    components: {
        Input,
        Textarea,
        InputFile,
        Button,
        ToggleButton
    },
    methods: {
      addItem(e){
        e.preventDefault();
          const res = axios.post(baseURL, { 
              titulo: this.titulo,
              sabor: this.sabor,
              preco: this.preco,
              descricao: this.descricao,
              imagem: this.imagem
          })
      
          this.itens = [...this.itens, res.data]
          
          this.titulo = '';
          this.sabor = '';
          this.preco = '';
          this.descricao = '';
          this.imagem = '';
        },
      deleteItem() {
        axios.delete(`http://localhost:3000/itens/2`);
      },
      getItem() {
        axios
          .get(`http://localhost:3000/itens`)
          .then((res) => {
            this.itens = res.data;
            console.log(res.data);
          })
      }
    },
    created() {
      /*this.getItem();*/
    },
    mounted (){
      itens.listar().then(resposta => {
        console.log(resposta.data)
        this.itens = resposta.data
      })
    }
}
</script>

<style>
  #form-pastel {
    position: absolute;
    width: 1140px;
    top: 73.5px;
    left: 20px;
  }

  .start-row {
    display: grid;
    grid-template-columns: 460px 480px 160px;
    grid-column-gap: 20px;
    height: 40px;
  }

  .middle-row {
    width: 100%;
    padding-top: 20px;
  }

  .end-row {
    width: 100%;
    height: 125px;
    padding-top: 15px;
  }

  input::placeholder,
  textarea::placeholder {        
    color: #A03400;
    font: normal normal normal 15.5px/20px Roboto;
  }
    
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
  }

.form {
    position: relative;
    top: 78px;
    left: 0;
    width: 1180px;
    height: 392px;
    background: #FFFFFF 0% 0% no-repeat padding-box;
    box-shadow: 0px 0px 30px #740B0B45;
    border-radius: 20px;
    opacity: 1;
    z-index: 0;
}

.form-header {
    display: flex;
    position: absolute;
    width: 100%;    
    height: 93px;
    background: #FFCA00 0% 0% no-repeat padding-box;
    border-radius: 20px 20px 0px 0px;
    opacity: 1;
}

.text-header {
    position: absolute;
    left: 60.5px;
    top: 25px;
    font: italic normal bold 22.5px/31px Roboto;
    letter-spacing: 0.5px;
    opacity: 1;
}

.switch {
    position: absolute;
    left: 983px;
    top: 27%;
    font: normal normal normal 17px/21px Roboto;
    letter-spacing: 0px;
    color: #A03400;
    opacity: 1;
}


</style>