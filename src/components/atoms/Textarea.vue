<template>
    <textarea 
      class="descricao-item"
      rows="3"
      @input="$emit('input', $event.target.value)"
    >
    </textarea>
</template>

<script>
export default {
    name: 'Textarea'
}
</script>

<style>
  .descricao-item {
      width: 100%;
      background: #FFFFFF 0% 0% no-repeat padding-box;
      border: 1px solid #E43636;
      border-radius: 10px;
      padding-left: 19.5px;  
      font: normal normal normal 16px/21px Roboto;
      padding-top: 10px;
      padding-bottom: 6px;
      resize: none;
}
</style>