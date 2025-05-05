<template>
  <div class="app-wrapper">
    <HeaderComp />
    <BunnerComp/>
  
  </div>
  
</template>

<script>

import HeaderComp from "./components/HeaderComp.vue";
import BunnerComp from "./components/BunnerComp.vue";
export default {
  name: "App",
  components: {
    HeaderComp,
    BunnerComp,
  },
};
</script>

<style lang="scss">
.app-wrapper {
  display: flex;
  flex-direction: column;
}


</style>
