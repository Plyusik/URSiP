<script setup lang="ts">
defineEmits(["filterParamChange"]);
const { filterParam } = defineProps(["filterParam"]);
</script>

<template>
   <aside class="left-col">
      <button class="left-col__new-btn">
         <div class="left-col__new-btn--icon-box">
            <img
               src="../assets/plus.png"
               alt="create new icon"
               class="left-col__new-btn--icon"
            />
         </div>
         Create new
      </button>
      <button
         class="left-col__filter-btn mb7"
         @click="$emit('filterParamChange', 'even')"
      >
         <div class="left-col__filter-btn--icon-box">
            <svg
               :class="{ 'filter-selected': filterParam === 'even' }"
               width="20"
               height="20"
               viewBox="0 0 20 20"
               fill="none"
               xmlns="http://www.w3.org/2000/svg"
            >
               <path
                  d="M11 -4.76837e-08V3.03C14.39 3.52 17 6.42 17 9.95C17 10.85 16.82 11.7 16.5 12.49L19.12 14.02C19.68 12.78 20 11.4 20 9.95C20 4.77 16.05 0.5 11 -4.76837e-08ZM10 16.95C8.14348 16.95 6.36301 16.2125 5.05025 14.8997C3.7375 13.587 3 11.8065 3 9.95C3 6.42 5.61 3.52 9 3.03V-4.76837e-08C3.94 0.5 0 4.76 0 9.95C0 12.6022 1.05357 15.1457 2.92893 17.0211C3.85752 17.9497 4.95991 18.6863 6.17317 19.1888C7.38642 19.6913 8.68678 19.95 10 19.95C13.3 19.95 16.23 18.34 18.05 15.86L15.45 14.33C14.17 15.95 12.21 16.95 10 16.95Z"
                  fill="#78909C"
               />
            </svg>
         </div>
         <div class="left-col__filter-btn--text-box">
            <p class="btn-caption">Even rows of data</p>
            <p class="btn-description">Display rows 2,4,6 etc</p>
         </div>
      </button>
      <button
         class="left-col__filter-btn"
         @click="$emit('filterParamChange', 'odd')"
      >
         <div class="left-col__filter-btn--icon-box">
            <svg
               :class="{ 'filter-selected': filterParam === 'odd' }"
               width="24"
               height="20"
               viewBox="0 0 24 20"
               fill="none"
               xmlns="http://www.w3.org/2000/svg"
            >
               <path
                  d="M19.78 4.76837e-08L24 4.22L8.44 19.8L0 11.35L4.22 7.13L8.44 11.35L19.78 4.76837e-08ZM19.78 2.8L8.44 14.16L4.22 9.99L2.81 11.35L8.44 16.97L21.19 4.22L19.78 2.8Z"
                  fill="#78909C"
               />
            </svg>
         </div>
         <div class="left-col__filter-btn--text-box">
            <p class="btn-caption">Odd rows of data</p>
            <p class="btn-description">Display rows 1,3,5 etc</p>
         </div>
      </button>
      <button
         class="left-col__filter-btn"
         @click="$emit('filterParamChange', 'all')"
      >
         <div class="left-col__filter-btn--icon-box">
            <svg
               :class="{ 'filter-selected': filterParam === 'all' }"
               width="20"
               height="18"
               viewBox="0 0 20 18"
               fill="none"
               xmlns="http://www.w3.org/2000/svg"
            >
               <path
                  d="M16 0H4V4H16V0ZM17 9C16.7348 9 16.4804 8.89464 16.2929 8.70711C16.1054 8.51957 16 8.26522 16 8C16 7.73478 16.1054 7.48043 16.2929 7.29289C16.4804 7.10536 16.7348 7 17 7C17.2652 7 17.5196 7.10536 17.7071 7.29289C17.8946 7.48043 18 7.73478 18 8C18 8.26522 17.8946 8.51957 17.7071 8.70711C17.5196 8.89464 17.2652 9 17 9ZM14 16H6V11H14V16ZM17 5H3C2.20435 5 1.44129 5.31607 0.87868 5.87868C0.316071 6.44129 0 7.20435 0 8V14H4V18H16V14H20V8C20 7.20435 19.6839 6.44129 19.1213 5.87868C18.5587 5.31607 17.7956 5 17 5Z"
                  fill="#78909C"
               />
            </svg>
         </div>
         <div class="left-col__filter-btn--text-box">
            <p class="btn-caption">All data</p>
            <p class="btn-description">Display all data</p>
         </div>
      </button>
   </aside>
</template>
<style scoped>
.left-col {
   position: relative;
   z-index: 5;
   display: flex;
   flex-direction: column;
   width: 260px;
   height: 100%;
   margin-left: 64px;
   margin-top: 32px;
}
.left-col__new-btn {
   width: 213px;
   align-self: center;
   padding: 12px 16px;
   margin-bottom: 24px;
   background: var(--white-color);
   box-shadow: 0px 16px 24px rgba(54, 123, 245, 0.16),
      0px 6px 12px rgba(54, 123, 245, 0.16);
   border: none;
   border-radius: 99px;
   font-family: "Quicksand";
   font-weight: 500;
   font-size: 20px;
   line-height: 28px;
   display: flex;
   gap: 8px;
   align-items: center;
   letter-spacing: 0.15px;
   color: var(--blue-color);
}
.left-col__new-btn--icon-box {
   display: flex;
   align-items: center;
   justify-content: center;
   width: 32px;
   height: 32px;
}
.left-col__new-btn--icon {
   width: 16px;
   height: 16px;
}
.left-col__filter-btn {
   display: flex;
   align-items: center;
   height: 56px;
   background: transparent;
   border: none;
   cursor: pointer;
}
.mb7 {
   margin-bottom: 7px;
}
.left-col__filter-btn--icon-box {
   display: flex;
   align-items: center;
   justify-content: center;
   width: 28px;
   height: 28px;
   margin-left: 12px;
}
.filter-selected path {
   fill: var(--blue-color);
}
.left-col__filter-btn--text-box {
   margin-left: 12px;
   padding: 7px 0;
   text-align: left;
}
.btn-caption {
   font-family: "Quicksand";
   font-weight: 500;
   font-size: 16px;
   line-height: 24px;
   letter-spacing: 0.44px;
   color: var(--black-color);
}
.btn-description {
   display: flex;
   align-items: flex-end;
   font-family: "Roboto";
   font-weight: 400;
   font-size: 12px;
   line-height: 16px;
   letter-spacing: 0.4px;
   color: var(--gray-color);
}
</style>
