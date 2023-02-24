<script setup lang="ts">
import { ref, provide } from "vue";
import Header from "./components/Header.vue";
import Subheader from "./components/Subheader.vue";
import LeftCol from "./components/LeftCol.vue";
import Center from "./components/Center.vue";
const filterParam = ref("all");
provide("filterParam", filterParam);
const changeFilter= (filter: string) => {
   filterParam.value = filter; 
}
</script>

<template>
   <div class="dashboard">
      <Header />
      <Subheader />
      <LeftCol @filterParamChange="changeFilter" :filterParam="filterParam"/>
      <Center />
   </div>
</template>
<style scoped>
.dashboard {
   position: absolute;
   width: 1440px;
   min-height: 574px;
   background-color: #e2f0f0;
   box-shadow: 0px 33px 43px rgba(0, 0, 0, 0.1),
      0px 9.94853px 12.9632px rgba(0, 0, 0, 0.0651589),
      0px 4.13211px 5.38427px rgba(0, 0, 0, 0.05),
      0px 1.4945px 1.94738px rgba(0, 0, 0, 0.0348411);
   border-radius: 20px;
   overflow: hidden;
   left: 50%;
   transform: translateX(-50%);
}
</style>
