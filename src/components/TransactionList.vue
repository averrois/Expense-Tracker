<script setup lang="ts">
import type { TransactionProps } from "@/components/types";

defineProps<{
  transactions: TransactionProps[];
}>();

const emit = defineEmits(['transactionDeleted'])

const deleteTransaction = (id: number) => {
  emit('transactionDeleted', id)
}

</script>

<template>
  <div class="mt-6">
    <h4 class="text-xl font-bold">History</h4>
    <ul class="space-y-4 mt-4">
      <li
        v-if="transactions"
        v-for="transaction in transactions"
        :key="transaction.id"
        class="flex items-center space-x-2"
      >
        <button
          class="w-12 h-12 rounded bg-grey-200 hover:bg-grey-200/40 transition-all"
          @click="deleteTransaction(transaction.id)"
        >
          <span
            class="rotate-45 inline-block transition-all hover:rotate-[-135deg] text-4xl font-semibold"
            >+</span
          >
        </button>
        <div
          class="ml-2 flex justify-between items-center w-full border-r-[5px] rounded"
          :class="
            transaction.amount < 0 ? 'border-red-500' : 'border-green-500'
          "
        >
          <span class="inline-block text-lg font-medium">{{
            transaction.text
          }}</span>
          <span class="inline-block text-lg font-extrabold mr-2">{{
            transaction.amount
          }}</span>
        </div>
      </li>
      <div class="w-full border-[1px] rounded border-grey-200" />
    </ul>
  </div>
</template>
