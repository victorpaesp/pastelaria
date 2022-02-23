<template>
    <div class="division">
        <div class="line-left"></div>
        <div class="text-center"> Veja como será apresentado ao cliente </div>
        <div class="line-right"></div>
    </div>   
</template>

<script>
export default {
    name: 'Division'
}
</script>

<style scoped>  
    .division {
        position: absolute;
        top: 852px;
        width: 100%;
        height: 29px;
        opacity: 1;
    }

    .line-left,
    .line-right {
        position: absolute;
        width: 705px;
        height: 0px;
        border: 1px solid #E43636;
        opacity: 1;
    }

    .line-left {
        left: 0;
    }

    .line-right { 
        left: 1215px;
    }

    .text-center {
        position: absolute;
        top: -12px;
        left: 755px;
        width: 410px;
        height: 29px;
        text-align: center;
        font: italic normal bold 23.5px/29px Roboto;
        letter-spacing: 0px;
        color: #A03400;
        opacity: 1;
    }

    .text-center p {
        padding: 0 10px;
    }
</style>