<template>
  <div>
    <img alt="wave-header" src="@/assets/img/wave.png" id="wave-header">
    <Parallax />
    <Logo />
    <Pasteis />
  </div>
</template>

<script>
import Logo from './Logo.vue';
import Parallax from './Parallax.vue';
import Pasteis from './Pasteis.vue';

export default {
  name: 'Wave',
  components: {
    Logo,
    Pasteis,
    Parallax
  }
}
</script>

<style scoped>
  img {
    position: absolute;
  }

  #wave-header {
    top: -0.578948974609375px;
    left: 0px;
    width: 1921px;
    height: 546px;
  }
</style>
