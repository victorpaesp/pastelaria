<template>
    <div>
        <input type="reset"  class="clear-btn"  value="LIMPAR" />
        <input type="submit" class="submit-btn" value="CADASTRAR" /> 
    </div>
</template>

<script>
export default {
    name: 'Button'
}
</script>

<style>
    .clear-btn {
        position: absolute;
        top: 290px;
        left: 353px;
        width: 200px;
        height: 60px;
        background: #E43636 0% 0% no-repeat padding-box;
        color: #FFFFFF;
        border: 0;
        border-radius: 30px;
        opacity: 1;
        text-align: center;
        letter-spacing: 0;
        padding-top: 3px;
        font: normal normal 900 21px/26px Roboto;
        cursor: pointer;
    }

    .submit-btn {
        position: absolute;
        top: 290px;
        left: 588px;
        width: 200px;
        height: 60px;
        background: #FFCA00 0% 0% no-repeat padding-box;
        color: #A03400;
        border: 0;
        border-radius: 30px;
        opacity: 1;
        text-align: center;
        letter-spacing: 0;
        padding-top: 3px;
        font: normal normal 900 21px/26px Roboto;
        cursor: pointer;
    }

    .clear-btn:hover,
    .submit-btn:hover {
    
      border: 2px solid transparent;
      outline-color: black;
      outline-offset: 15px;
    }

</style>