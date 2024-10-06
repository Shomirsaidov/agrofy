<template>
  <div>
    <router-view style="position: relative; z-index: 4; margin-bottom: 40px;" />
    <Footerik/>
  </div>
</template>


<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  z-index: 0;
  position: relative;
}
</style>


<script>

import Footerik from '@/components/Footer.vue'

export default {
  components: {
    Footerik
  }
}


</script>
