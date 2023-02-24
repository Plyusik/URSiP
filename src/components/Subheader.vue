<script setup lang="ts"></script>

<template>
   <div class="subheader">
      <nav class="tabs">
         <a href="#" class="tabs__item tabs__item--active">Analyze</a>
         <a href="#" class="tabs__item">My campaigns</a>
         <a href="#" class="tabs__item">Configure</a>
      </nav>
   </div>
</template>
<style scoped>
.subheader {
   background: var(--white-color);
   width: 1440px;
   height: 56px;
   border-bottom: 1px dashed var(--gray-light-color);
}
.tabs {
   position: absolute;
   left: 376px;
   width: 687px;
   font-size: 16px;
   line-height: 24px;
   display: flex;
   text-align: center;
   letter-spacing: 0.44px;
   z-index: 5;
}
.tabs__item {
   height: 56px;
   display: flex;
   justify-content: center;
   align-items: center;
   padding: 16px 12px;
   text-decoration: none;
   color: var(--gray-color);
}
.tabs__item--active {
   border: var(--gray-border);
   border-bottom: 1px solid var(--white-color);
   border-radius: 4px 4px 0px 0px;
   color: var(--black-color);
}
</style>
