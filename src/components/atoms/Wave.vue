<template>
  <div>
    <img alt="wave-header" src="@/assets/img/wave.png" id="wave-header">
    <Logo />
    <Pasteis />
  </div>
</template>

<script>
import Logo from './Logo.vue';
import Pasteis from './Pasteis.vue';

export default {
  name: 'Wave',
  components: {
    Logo,
    Pasteis
  }
}
</script>

<style scoped>
  img {
    position: absolute;
  }

  #wave-header {
    width: 100%;
  }
</style>
