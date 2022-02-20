<template>
<div>
  <button class="clear"  v-on:click="clear">LIMPAR </button>
  <input type="submit" class="submit-btn" value="CADASTRAR" /> 
</div>
</template>

<script>
export default {
    name: 'Button',
    methods: {
        clear: function () {
            alert('Teste de click');
        }
    }
}
</script>

<style>
.clear {
   /* Layout Properties */
    position: absolute;
    top: 110%;
    left: 31.5%;
    width: 17%;
    height: 22.2%;
    /* UI Properties */
    background: #E43636 0% 0% no-repeat padding-box;
    color: #FFFFFF;
    border: 0;
    border-radius: 30px;
    opacity: 1;
    text-align: center;
    letter-spacing: 0;
    font: normal normal 900 20px/26px Roboto;
}

.submit-btn {
    position: absolute;
    top: 110%;
    left: 51.5%;
    width: 17%;
    height: 22.2%;
    background: #FFCA00 0% 0% no-repeat padding-box;
    color: #A03400;
    border: 0;
    border-radius: 30px;
    opacity: 1;
    text-align: center;
    letter-spacing: 0;
    font: normal normal 900 20px/26px Roboto;
}

</style>