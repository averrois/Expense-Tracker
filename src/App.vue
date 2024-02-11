<script setup lang="ts">
import { ref } from "vue"
import Header from "@/components/Header.vue"
import Balance from "@/components/Balance.vue"
import IncomeExpenses from "@/components/IncomeExpenses.vue"
import TransactionList from "@/components/TransactionList.vue"
import AddTransaction from "@/components/AddTransaction.vue"

const transactions = ref([
  {
    id: 1,
    text: "Salary",
    amount: -5000,
  },
  {
    id: 2,
    text: "Book",
    amount: -1000,
  },
  {
    id: 3,
    text: "Camera",
    amount: 800,
  },
])
</script>

<template>
  <main
    class="border-[2px] text-left max-sm:w-full border-grey-200 bg-grey-100 px-6 py-2 rounded mx-auto w-[500px]"
  >
    <Header />
    <Balance />
    <IncomeExpenses />
    <TransactionList :transactions="transactions"/>
    <AddTransaction />
  </main>
</template>
