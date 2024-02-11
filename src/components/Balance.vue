<script setup lang="ts">
defineProps({
  balance: {
    type: Number,
    default: 0,
  },
});
</script>

<template>
  <h4 class="text-lg font-bold mb-2 mt-2">Your Balance</h4>
  <h2 class="text-3xl font-extrabold">{{ balance }}$</h2>
</template>
