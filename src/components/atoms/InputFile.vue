<template>
    <div class="dropbox">
        <input 
          type="file" 
          accept="image/*" 
          class="input-file"
        />
        <p>
            <i class="bi bi-image"></i> <br> Jogue aqui o arquivo de imagem do seu pastel ou clique para localizar a pasta.
        </p>
    </div>
</template>

<script>
export default {
    name: 'InputFile'
}
</script>

<style>
    .dropbox {
        height: 100%;
        cursor: pointer;
        border: 1px solid #E43636;
        border-radius: 10px;
        opacity: 1;
        font: normal normal normal 15.7px/21px Roboto;
        opacity: 1;
        display: flex;
        align-items: center;
        color: #A03400;
    }

    .dropbox p {
        text-align: center;
        line-height: 30px;
    }
  
    .input-file {
        opacity: 0;
        position: absolute;
        cursor: pointer;
    }

    .bi.bi-image {
        font-size: 49px;
        color: #E43636;
    }
</style>