<template>
    <div class="form">
        <div class="formHeader">
            <p class="text-header">Monte aqui o seu cardápio. O que está esperando?</p>
            <p class="switch"> 
                <ToggleButton />
            </p>
        </div>
    <Formulario />
    </div>
</template>

<script>
import ToggleButton from '@/components/atoms/ToggleButton.vue';
import Formulario from '@/components/molecules/Formulario.vue';



export default {
    name: 'Form',
    data() {
        return {
            enabled: false
        }
    },
    components: {
        Formulario,
        ToggleButton
    }
}
</script>

<style>

.form {
    position: absolute;
    top: 346.5px;
    left: 370px;
    width: 1180px;
    height: 392px;
    background: #FFFFFF 0% 0% no-repeat padding-box;
    box-shadow: 0px 0px 30px #740B0B45;
    border-radius: 20px;
    opacity: 1;
    z-index: 0;
}

.formHeader {
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