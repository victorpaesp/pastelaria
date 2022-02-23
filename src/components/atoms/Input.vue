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
        border: 1px solid #E43636;
        border-radius: 10px;
        opacity: 1;
        padding-left: 19.5px; 
        font: normal normal normal 16px/21px Roboto;
        opacity: 1;
}
</style>