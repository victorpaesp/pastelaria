<template>
  <div class="form">
        <div class="formHeader">
            <p class="text-header">Monte aqui o seu cardápio. O que está esperando?</p>
            <p class="switch">Comida Bebida</p>
        </div>
  <Formulario />
  </div>
</template>

<script>

import Formulario from '@/components/molecules/Formulario.vue';

export default {
    name: 'Form',
    components: {
        Formulario
    }
}
</script>

<style>

.form {
    position: absolute;
    top: 36.8%;
    left: 19.4%;
    width: 61.4%;
    height: 41.3%;
    background: #FFFFFF 0% 0% no-repeat padding-box;
    box-shadow: 0px 0px 30px #740B0B45;
    border-radius: 20px;
    opacity: 1;
}

.formHeader {
    display: flex;
    position: absolute;
    width: 100%;
    height: 23.7%;
    background: #FFCA00 0% 0% no-repeat padding-box;
    border-radius: 20px 20px 0px 0px;
    opacity: 1;
}

.text-header {
    position: absolute;
    left: 4.8%;
    top: 27%;
    font: italic normal bold 24px/29px Roboto;
    letter-spacing: 0px;
    opacity: 1;
}

.switch {
    position: absolute;
    left: 90%;
    top: 27%;
    font: normal normal normal 16px/21px Roboto;
    letter-spacing: 0px;
    color: #A03400;
    opacity: 1;
}



</style>