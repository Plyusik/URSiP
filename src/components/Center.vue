<script setup lang="ts">
import Table from "./Table.vue";
</script>

<template>
   <div class="center">
      <div class="center-header">
         <h4 class="center-header__h4">Dashboard</h4>
         <div class="center-header__controls">
            <div class="center-header__dates">
               <p>Aug 21, 2021 · Sep 21 2021</p>
               <div class="center-header__dates--arrow"></div>
            </div>
            <button class="center-header__btn">
               <img src="../assets/printer_.svg" alt="print" />
            </button>
            <button class="center-header__btn">
               <img src="../assets/export_.svg" alt="export" />
            </button>
         </div>
      </div>
      <Table />
   </div>
</template>
<style scoped>
.center {
   position: absolute;
   padding-top: 40px;
   left: 14.17%;
   right: 3.89%;
   top: 92px;
   bottom: 28px;
   width: 1180px;
   height: 454px;
   padding-left: 196px;
}
.center-header {
   display: flex;
   justify-content: space-between;
   margin-bottom: 33px; 
}
.center-header__h4 {
   font-family: "Quicksand";
   font-weight: 500;
   font-size: 34px;
   line-height: 42px;
   letter-spacing: 0.25px;
   color: var(--black-color);
}
.center-header__controls {
   display: flex;
   align-self: end;
}
.center-header__dates {
   position: relative;
   display: flex;
   align-items: center;
   justify-content: space-between;
   padding: 0 12px;
   width: 232px;
   height: 32px;
   background-color: transparent;
   border: var(--gray-border);
   border-radius: 10px;
   font-weight: 400;
   font-size: 14px;
   line-height: 20px;
   letter-spacing: 0.25px;
   color: var(--black-color);
}
.center-header__dates--arrow {
   width: 0;
   height: 0;
   border: 5px solid transparent;
   border-top: 5px solid #78909c;
   margin-right: 5px;
   transform: translateY(25%);
}
.center-header__btn {
   width: 32px;
   height: 32px;
   margin-left: 8px;
   border: none;
   border-radius: 4px;
   background: var(--whitish-color);
}
.center-header__btn:last-of-type {
   margin-right: 64px;
}
</style>
