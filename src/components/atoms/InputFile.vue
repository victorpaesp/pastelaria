<template>
    <div class="dropbox">
          <input type="file" 
            accept="image/*" class="input-file">
            <p>
            <i class="bi bi-image"></i><br> Jogue aqui o arquivo de imagem do seu pastel ou clique para localizar a pasta.
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
    width: 100%;
    height: 100%;
    cursor: pointer;
    border: 1px solid #E43636;
    border-radius: 10px;
    opacity: 1;
    font: normal normal normal 15.7px/21px Roboto;
    letter-spacing: 0px;
    opacity: 1;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    color: #A03400;
  }
  
  .input-file {
    opacity: 0;
    width: 100%;
    height: 48%;
    position: absolute;
    cursor: pointer;
  }
  
  .dropbox p {
    text-align: center;
    line-height: 30px;
  }

  .bi.bi-image {
    font-size: 49px;
    color: #E43636;
  }

</style>