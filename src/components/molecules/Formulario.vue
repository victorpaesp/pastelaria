<template>
  <div>
      <form action="" id="form-pastel" @submit="criarItem">
        <div class="start-row">
            <Input id="titulo" name="titulo" v-model="titulo" placeholder="Título do Pedido"/>
            <Input id="sabor"  name="sabor"  v-model="sabor"  placeholder="Sabor"/>
            <Input id="preco"  name="preco"  v-model="preco"  placeholder="R$" step="0.01" min="0.01"/>
        </div>
        <div class="middle-row">
            <Textarea id="descricao" name="descricao" v-model="descricao" placeholder="Descrição" />
        </div>
        <div class="end-row">
            <InputFile /> 
        </div>

        <Button />
    </form>
  </div>
</template>

<script>
import Input from '@/components/atoms/Input.vue';
import Textarea from '@/components/atoms/Textarea.vue';
import InputFile from '@/components/atoms/InputFile.vue';
import Button from '@/components/atoms/Button.vue';

export default {
    name: 'Formulario',
    data() {
        return {
            titulo: null,
            sabor: null,
            preco: null,
            descricao: null,
            imagem: null,
            msg: null
        }
    },
    components: {
        Input,
        Button,
        Textarea,
        InputFile
    },
    methods: {
        async criarItem (e) {
            e.preventDefault();

            const data = {
                titulo:    this.titulo,
                sabor:     this.sabor,
                preco:     this.preco,
                descricao: this.descricao

            }
            
            console.log(data);
        }
    }
}
</script>

<style>
    #form-pastel {
        display: grid;
        grid-template-rows: 15% 32% 43%;
        grid-row-gap: 1em;
        position: absolute;
        height: 68%;
        width: 96%;
        top: 18%;
        left: 2%;
    }

    .start-row {
        display: grid;
        width: 100%;
        grid-template-columns: 1.3fr 1.3fr 0.4fr;
        grid-column-gap: 18px;
    }

    .middle-row,
    .end-row {
        display: grid;
        width: 100%;
    }

    input::placeholder,
    textarea::placeholder {        
      color: #A03400;
    }
</style>