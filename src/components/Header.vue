<script setup lang="ts">
</script>

<template>
   <header class="header">
      <div class="header__logo">
         <img src="../assets/logo_dashboard.png" alt="dashboard logo" />
      </div>
      <div class="header__right">
         <button class="header-btn header__right--help">
            Help
            <img src="../assets/help-circle.png" alt="help circle" />
         </button>
         <button class="header-btn header__right--upgrade">Upgrade</button>
         <img
            src="../assets/userpic.png"
            alt="userpic"
            class="header__right--userpic"
         />
      </div>
   </header>
</template>
<style scoped>
.header {
   display: flex;
   justify-content: space-between;
   background: var(--white-color);
   width: 1440px;
   height: 64px;
   padding: 12px 16px;
}
.header-btn {
   width: 96px;
   height: 40px;
   font-family: "Roboto";
   padding: 8px 9px;
   border: none;
   border-radius: 10px;
}
.header__right {
   display: flex;
   gap: 16px;
}
.header__right--help {
   font-weight: 400;
   font-size: 16px;
   line-height: 24px;
   letter-spacing: 0.44px;
   display: flex;
   justify-content: space-between;
   align-items: center;
   background-color: var(--whitish-color);
   color: var(--gray-color);
}
.header__right--upgrade {
   font-weight: 500;
   font-size: 14px;
   line-height: 16px;
   letter-spacing: 0.75px;
   text-transform: uppercase;
   box-shadow: 0px 4px 8px rgba(54, 123, 245, 0.16),
      0px 2px 4px rgba(54, 123, 245, 0.24);
   background-color: var(--white-color);
   color: var(--blue-color);
}
.header__userpic {
   height: 40px;
   width: 40px;
}
</style>
