<script setup lang="ts">
defineProps({
  income: {
    type: Number,
    default: 0,
  },
  expenses: {
    type: Number,
    default: 0,
  },
});
</script>

<template>
  <div
    class="flex justify-between items-center w-full mt-8 bg-black rounded-lg p-4"
  >
    <div class="w-1/2 text-center">
      <h4 class="text-lg uppercase font-bold">Income</h4>
      <p id="money-plus" class="text-3xl mt-3 font-extrabold text-green-500">+${{ income }}</p>
    </div>
    <div class="w-1/2 text-center">
      <h4 class="text-lg uppercase font-bold">Expense</h4>
      <p id="money-minus" class="text-3xl mt-3 font-extrabold text-red-500">
        -${{ expenses }}
      </p>
    </div>
  </div>
</template>
