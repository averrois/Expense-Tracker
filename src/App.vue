<script setup lang="ts">
import Header from "@/components/Header.vue";
import Balance from "@/components/Balance.vue";
import IncomeExpenses from "@/components/IncomeExpenses.vue";
import TransactionList from "@/components/TransactionList.vue";
import AddTransaction from "./components/AddTransaction.vue";
</script>

<template>
  <main
    class="border-[2px] text-left max-sm:w-full border-grey-200 bg-grey-100 px-6 py-2 rounded mx-auto w-[500px]"
  >
    <Header />
    <Balance />
    <IncomeExpenses />
    <TransactionList />
    <AddTransaction />
  </main>
</template>
