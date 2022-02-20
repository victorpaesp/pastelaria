<template>
  <div class="backgroundShadow"></div>
</template>

<script>

export default {
  name: 'Background',
  components: {
  }
}
</script>

<style scoped>
  .backgroundShadow {
      position: absolute;
      top: 0px;
      left: 0px;
      width: 1920px;
      height: 1233px;
      /* UI Properties */
      background: transparent radial-gradient(closest-side at 50% 50%, #FFFFFF 0%, #FFFFFF 67%, #FFFFFF00 100%) 0% 0% no-repeat padding-box;
      opacity: 1;
  }
</style>
