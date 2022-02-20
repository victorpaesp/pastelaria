<template>
  <div>
      <form action="." id="form-pastel"  @submit="addItem">
        <div class="start-row">
            <Input id="titulo" name="titulo" v-model="titulo" placeholder="Título do Pedido"/>
            <Input id="sabor"  name="sabor"  v-model="sabor" placeholder="Sabor"/>
            <Input id="preco"  name="preco"  v-model="preco" placeholder="R$" step="0.01" min="0.01"/>
        </div>
        <div class="middle-row">
            <Textarea id="descricao" name="descricao" v-model="descricao" placeholder="Descrição" />
        </div>
        <div class="end-row">
            <InputFile /> 
        </div>
    <Button />

    </form>
    
    <!--<button style="height: 200px; width: 200px; position: absolute; top: 200px;" @click="deleteProduct()">Delete</button>-->
  </div>
</template>

<script>
import axios from 'axios';
import Button from '@/components/atoms/Button.vue'
import Input from '@/components/atoms/Input.vue';
import Textarea from '@/components/atoms/Textarea.vue';
import InputFile from '@/components/atoms/InputFile.vue';

const baseURL = "http://localhost:3000/itens";

export default {
    name: 'Formulario',
    data() {
        return {
            itens: [],
            itemTeste: '',
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
        Button
    },
  /*  async created() {
    try {
      const res = await axios.get(`baseURL`);
      this.itens = res.data; 
    } catch (e) {
      console.error(e);
    }
  },*/
    methods: {
        async addItem(){
            const res = await axios.post(baseURL, { 
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
        deleteProduct() {
            axios.delete(`http://localhost:3000/itens/2`);
        }
    }
}
</script>

<style>
    #form-pastel {
        position: absolute;
        width: 1140px;
        top: 73px;
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

</style>