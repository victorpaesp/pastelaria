<template>
    <div class="division">
        <div class="lineLeft"></div>
        <div class="textCenter"> Veja como será apresentado ao cliente </div>
        <div class="lineRight"></div>
    </div>   
</template>

<script>
export default {
  name: 'Logo'
}
</script>

<style scoped>  
  .division {
        position: absolute;
        top: 852px;
        left: 0px;
        width: 100%;
        height: 29px;
        opacity: 1;
  }

    .lineLeft,
    .lineRight {
            position: absolute;
            top: 0;
            width: 705px;
            height: 0px;
            /* UI Properties */
            border: 1px solid #E43636;
            opacity: 1;
    }

    .lineLeft {
        left: 0;
    }

    .lineRight { 
        left: 1215px;
    }

  .textCenter {
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

    .textCenter p {
        padding: 0 10px;
    }
</style>
