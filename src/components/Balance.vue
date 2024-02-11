<script setup lang="ts">
defineProps({
  total: {
    type: Number,
    default: 0,
  },
});
</script>

<template>
  <h4 class="text-lg font-bold mb-2 mt-2">Your Balance</h4>
  <h2 class="text-3xl font-extrabold">${{ total }}</h2>
</template>
