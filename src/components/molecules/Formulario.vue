<template>
  <div>
    <div class="form">
        <div class="form-header">
            <p class="text-header">Monte aqui o seu cardápio. O que está esperando?</p>
            <p class="switch"> 
                <ToggleButton />
            </p>
        </div>
        
        <div id="form-pastel" > 
            <div class="start-row">
                <Input id="titulo" name="titulo" v-model="titulo" placeholder="Título do pedido"/>
                <Input id="sabor"  name="sabor"  v-model="sabor"  placeholder="Sabor"/>
                <Input id="preco"  name="preco"  v-model="preco"  placeholder="R$" />
            </div>
            <div class="middle-row">
                <Textarea id="descricao" name="descricao" v-model="descricao" placeholder="Descrição" />
            </div>
            <div class="end-row">
                <InputFile id="imagem" name="imagem" v-model="imagem" /> 
            </div>
     <!--   <Testando />  -->
      <Button @on-click="createItem" />
        <p v-if="errors.length">
    <b>Please correct the following error(s):</b>
    <ul>
      <li v-for="error in errors" :key="error">{{ error }}</li>
    </ul>
  </p>
 
        </div>
    </div>


   <div class="card" v-for="comida in comidasData" :key="comida.id">
        <div class="item">
            <div class="item-header">
                 <p class="titulo-pedido">"{{ comida.titulo }}"</p>
                 <p class="preco-pedido">R$ {{ comida.preco }}</p>
            </div>
            <div class="imagem-item">{{ comida.imagem }}</div>
            <p class="sabor-pedido">Sabor: <span class="pedido-res">{{ comida.sabor }}</span></p>
            <p class="descricao-pedido">Descrição: <span class="pedido-res">{{ comida.descricao }}</span></p>
        <button class="del" @click="deleteItem(comida.id)">x</button>
        </div>
    </div>
  </div>
</template>

<script>
/*import axios from 'axios';*/
import Button from '@/components/atoms/Button.vue';
import Input from '@/components/atoms/Input.vue';
import Textarea from '@/components/atoms/Textarea.vue';
import InputFile from '@/components/atoms/InputFile.vue';
/*import Card from '@/components/molecules/Card.vue'*/


import ToggleButton from '@/components/atoms/ToggleButton.vue';
/*import Testando from '@/components/molecules/Testando.vue'*/
import firebase from "../../firebaseInit";

const db = firebase.firestore();

/*const baseURL = "http://localhost:3000/itens";*/



export default {
    name: 'Formulario',
    data() {
        return {
            comidas: [],
            id: '',
            titulo: '',
            sabor: '',
            preco: null,
            descricao: null,
            imagem: '',
            errors: [],
            comidasData: []
        }
    },
    components: {
        Input,
        Textarea,
        InputFile,
        Button,
        ToggleButton,
        /*Testando*/
    },
    methods: {
    /*  addItem(e){

          if (this.titulo != null && this.sabor != null && this.preco != null) {
                const res = axios.post(baseURL, { 
                                  id: this.id,
                                  titulo: this.titulo,
                                  sabor: this.sabor,
                                  preco: this.preco,
                                  descricao: this.descricao,
                                  imagem: this.imagem
                              })
      
                this.itens = [...this.itens, res.data];
              }

              this.errors = [];

              if (this.titulo == null || this.titulo == '') {
                this.errors.push('Coloque um título do pedido');
                 e.preventDefault();
              }
              if (this.sabor == null || this.sabor == '') {
                this.errors.push('Coloque o sabor');
                 e.preventDefault();
              }
              if (this.preco == null || this.preco == '') {
                this.errors.push('Coloque o preço');
                 e.preventDefault();
              }
        },
        deleteItem(id) {
            this.$swal({
              title: 'Tem certeza?',
              text: 'Esta ação não poderá ser desfeita',
              type: 'warning',
              showCancelButton: true,
              confirmButtonText: 'Sim',
              cancelButtonText: 'Cancelar',
              showCloseButton: true,
              showLoaderOnConfirm: true
            }).then((result) => {
              if(result.value) {
                axios.delete(`http://localhost:3000/itens/${id}`);
          } 
        })
        },*/
        createItem() {
            if (this.titulo != '' && this.sabor != '' && this.preco != '') {
                db.collection("comidas")
                .add({ titulo: this.titulo, sabor: this.sabor, preco: this.preco, descricao: this.descricao })
                .then(() => {
                    console.log("Document successfully written!");
                   // this.readEmployees();
                })
                .catch((error) => {
                    console.error("Error writing document: ", error);
                });

                this.titulo = "";
                this.sabor = "";
                this.preco = "";
                this.descricao = "";
            }
        },
        deleteItem(id) {
            db.collection("comidas")
            .doc(id)
            .delete()
            .then(() => {
              console.log("Document successfully deleted!");
            })
            .catch((error) => {
              console.error("Error removing document: ", error);
        });
    }
    },
    created() {
      this.comidasData = [];
      db.collection("comidas")
        .get()
        .then((querySnapshot) => {
          querySnapshot.forEach((doc) => {
           this.comidasData.push({
              id: doc.id,
              titulo: doc.data().titulo,
              sabor: doc.data().sabor,
              preco: doc.data().preco,
              descricao: doc.data().descricao,
            });
            console.log(doc.id, " => ", doc.data());
          });
        })
        .catch((error) => {
          console.log("Error getting documents: ", error);
        });
    }
  
}
</script>

<style>
  #form-pastel {
    position: absolute;
    width: 1140px;
    top: 73.5px;
    left: 20px;
    z-index: 2;
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
    z-index: 2;
}

.switch {
    position: absolute;
    left: 983px;
    top: 27%;
    font: normal normal normal 17px/21px Roboto;
    letter-spacing: 0px;
    color: #A03400;
    opacity: 1;
    z-index: 2;
}

.card {
        position: relative;
        top: 277px;
        left: 60px;
        height: 270px;      
    }

    .item {
        position: absolute;
        top: 0;
        left: 420px;
        width: 1070px;
        height: 221px;
        background: #FFFFFF 0% 0% no-repeat padding-box;
        box-shadow: 0px 0px 30px #740B0B45;
        border-radius: 20px;
        opacity: 1;
    }

    .item-header {
        display: flex;
        width: 100%;
        height: 80px;
        background: #E43636 0% 0% no-repeat padding-box;
        border-radius: 20px 20px 0px 0px;
        opacity: 1;
    }

    .titulo-pedido {
        position: absolute;
        top: 20px;
        font: italic normal bold 30px/37px Roboto;
        letter-spacing: 0px;
        color: #FFCA00;
        opacity: 1;
        padding-left: 110px;
    }

    .preco-pedido {
        position: absolute;
        top: 20px;
        left: 930px;
        font: italic normal bold 24px/37px Roboto;
        letter-spacing: 0px;
        color: #FFFFFF;
        opacity: 1;
    }

    .sabor-pedido {
        position: absolute;
        top: 110px;
        left: 0;
        text-align: center;
        font: italic normal bold 23px/37px Roboto;
        letter-spacing: 1px;
        color: #A03400;
        opacity: 1;
        padding-left: 110px;
    }

    .pedido-res {
        font-weight: normal;
        font-style: normal;
    }

    .descricao-pedido {
        position: absolute;
        top: 155px;
        left: 0;
        text-align: center;
        font: italic normal bold 23px/37px Roboto;
        letter-spacing: 0px;
        color: #A03400;
        opacity: 1;
        padding-left: 110px;
    }

    .imagem-item {
        position: absolute;
        top: 50%;
        left: -110px;
        transform: translate(0%, -50%);
        width: 180px;
        height: 180px;
        background-color: #FFF;
        box-shadow: 0px 0px 30px #740B0B45;
        border-radius: 10px;
        opacity: 1;
    }

    .del {
      position: absolute;
      top: 90%;
      left: 98%;
      border: 0;
      border-radius: 5px;
      background-color: #E43636;
      height: 35px;
      width: 35px;
      cursor: pointer;
      color: #fff;
      font-size: 20px;
    }

    .del:hover {     
      border: 1px solid;
      outline-color: black;
      outline-offset: 15px;
    }
</style>