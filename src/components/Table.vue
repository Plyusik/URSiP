<script setup lang="ts">
import { ref, computed, inject } from "vue";
import { Ref } from "vue";
const headers = [
   "Data",
   "Summary1",
   "Summary2",
   "Summary3",
   "Summary4",
   "Summary5",
];
const table_data = [
   { data: "Data1", sum1: 186, sum2: 186, sum3: 92, sum4: 8, sum5: 1 },
   { data: "Data2", sum1: 95, sum2: 95, sum3: 31, sum4: 11, sum5: 0 },
   { data: "Data3", sum1: 329, sum2: 329, sum3: 256, sum4: 32, sum5: 4 },
   { data: "Data4", sum1: 804, sum2: 804, sum3: 697, sum4: 40, sum5: 22 },
];

const filterParam: Ref<string> = inject("filterParam", ref("all"));
const sortDesc = ref(true);
const srchValueObj = ref({
   data: "",
   sum1: "",
   sum2: "",
   sum3: "",
   sum4: "",
   sum5: "",
});

const filteredData = computed(() => {
   return (
      table_data
         .filter(
            (item) =>
               item.data.includes(srchValueObj.value.data) &&
               item.sum1.toString().includes(srchValueObj.value.sum1) &&
               item.sum2.toString().includes(srchValueObj.value.sum2) &&
               item.sum3.toString().includes(srchValueObj.value.sum3) &&
               item.sum4.toString().includes(srchValueObj.value.sum4) &&
               item.sum5.toString().includes(srchValueObj.value.sum5)
         )
         .filter((item, i) => {
            if (filterParam.value === "even") {
               return i % 2 ? item : null;
            } else if (filterParam.value === "odd") {
               return i % 2 ? null : item;
            } else {
               return item;
            }
         })
   );
});
const sortedData = computed(() => {
   return filteredData.value.sort((a, b) => {
      if (sortDesc.value) {
         return a.data > b.data ? 1 : -1;
      } else {
         return a.data > b.data ? -1 : 1;
      }
   });
});
</script>

<template>
   <table class="table">
      <thead class="table__header">
         <tr>
            <td v-for="item in headers" :key="item">
               <div
                  v-if="item === 'Data'"
                  @click="sortDesc = !sortDesc"
                  class="table__header--sort"
               >
                  <svg
                     :class="[{ 'sort-selected': !sortDesc }, 'arrow-up']"
                     width="10"
                     height="6"
                     viewBox="0 0 10 6"
                     fill="none"
                     xmlns="http://www.w3.org/2000/svg"
                  >
                     <path
                        d="M4.59 2.83L7.76 6L9.17 4.59L4.59 0L0 4.59L1.42 6L4.59 2.83Z"
                        fill="#C6CACC"
                     />
                  </svg>
                  <svg
                     :class="[{ 'sort-selected': sortDesc }, 'arrow-down']"
                     width="10"
                     height="6"
                     viewBox="0 0 10 6"
                     fill="none"
                     xmlns="http://www.w3.org/2000/svg"
                  >
                     <path
                        d="M1.42001 0L4.59001 3.17L7.76001 0L9.18001 1.41L4.59001 6L0.0100098 1.41L1.42001 0Z"
                        fill="#C6CACC"
                     />
                  </svg>
               </div>
               {{ item }}
            </td>
         </tr>
      </thead>
      <tbody class="table__body">
         <tr v-for="item in sortedData" key="item.data">
            <td v-for="(value, key, _) in item" :key="key">{{ value }}</td>
         </tr>
      </tbody>
      <tfoot>
         <tr>
            <td v-for="(item, index) in headers" :key="item">
               <template v-if="item === 'Data'">
                  <input
                     class="table__foot-srch"
                     type="text"
                     placeholder="Search..."
                     v-model="srchValueObj.data"
                  />
               </template>
               <input
                  v-else
                  type="text"
                  class="table__foot-srch--val"
                  v-model.number="srchValueObj[`sum${index}` as keyof typeof srchValueObj]"
               />
            </td>
         </tr>
      </tfoot>
   </table>
</template>
<style scoped>
.table {
   width: 920px;
   max-height: 304px;
}
tr {
   width: 100%;
   height: 64px;
   display: flex;
   justify-content: end;
   align-items: center;
}
thead tr {
   height: 48px;
   border-bottom: 2px solid var(--gray-light-color);
}
tr:not(:last-child) {
   border-bottom: 2px solid var(--gray-light-color);
}
td {
   position: relative;
   flex: 1 1 0;
}
td:first-child {
   min-width: 330px;
   text-align: start;
}
thead td:first-child {
   padding-left: 24px;
}
.table__body td:first-child {
   color: var(--black-color);
}
.table__header {
   font-family: "Quicksand";
   font-weight: 500;
   font-size: 16px;
   line-height: 24px;
   display: flex;
   align-items: center;
   text-align: right;
   letter-spacing: 0.44px;
   color: #919699;
}
.table__body {
   font-weight: 500;
   font-size: 20px;
   line-height: 28px;
   text-align: right;
   letter-spacing: 0.15px;
   color: var(--gray-color);
}
.table__header--sort {
   width: 32px;
   height: 32px;
   position: absolute;
   left: 0;
   cursor: pointer;
}
.arrow-up,
.arrow-down {
   position: absolute;
}
.arrow-up {
   top: calc(50% - 6px / 2 - 5px);
}
.arrow-down {
   top: calc(50% - 6px / 2 + 5px);
}
.sort-selected path {
   fill: #069697;
}
tfoot tr {
   align-items: start;
}
.table__foot-srch,
.table__foot-srch--val {
   height: 32px;
   padding: 0 12px;
   background-color: transparent;
   border: var(--gray-border);
   border-radius: 10px;
   font-family: "Roboto";
   font-weight: 400;
   font-size: 14px;
   line-height: 20px;
   letter-spacing: 0.25px;
   color: var(--black-color);
}
.table__foot-srch {
   width: 330px;
}
.table__foot-srch--val {
   width: 86px;
   margin-left: 32px;
}
::placeholder {
   color: var(--black-color);
}
</style>
