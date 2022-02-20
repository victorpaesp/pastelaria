<template>
  <input type="text" class="input" @input="$emit('input', $event.target.value)" />
</template>

<script>
export default {
    name: 'Input',
}
</script>

<style>
  .input {
      width: 100%;
      background: #FFFFFF 0% 0% no-repeat padding-box;
      border: 1px solid #E43636;
      border-radius: 10px;
      opacity: 1;
      padding-left: 19.5px;    
      text-align: left;
      font: normal normal normal 16px/21px Roboto;
      letter-spacing: 0px;
      opacity: 1;
}
</style>