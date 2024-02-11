<script setup lang="ts">
import { computed, ref } from "vue";
import Header from "@/components/Header.vue";
import Balance from "@/components/Balance.vue";
import IncomeExpenses from "@/components/IncomeExpenses.vue";
import TransactionList from "@/components/TransactionList.vue";
import AddTransaction from "@/components/AddTransaction.vue";
import { useToast } from "vue-toastification";

const toast = useToast()

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
]);

const total = computed(() => {
  return transactions.value.reduce((acc, transaction) => {
    return acc + transaction.amount;
  }, 0);
});

// Get income
const income = computed(() => {
  return transactions.value
    .filter((transaction) => transaction.amount > 0)
    .reduce((acc, transaction) => {
      return acc + transaction.amount;
    }, 0)
    .toFixed(2);
});

const expense = computed(() => {
  return transactions.value
    .filter((transaction) => transaction.amount < 0)
    .reduce((acc, transaction) => {
      return acc + transaction.amount;
    }, 0) * -1
    .toFixed(2);
});

const generateUniqueId = () => {
  return Math.floor(Math.random() * 1000000000);
};

// Add transaction
const handleTransactionSubmitted = (transactionData: any) => {
  transactions.value.push({
    id: generateUniqueId(),
    ...transactionData,
  });

  toast.success("Transaction added successfully")
}


// Delete Transaction
const handleTransactionDeleted = (id: number) => {
  transactions.value = transactions.value.filter(
    (transaction) => transaction.id !== id
  );

  toast.success("Transaction deleted successfully")
}
</script>

<template>
  <main
    class="border-[2px] text-left max-sm:w-full border-grey-200 bg-grey-100 px-6 py-2 rounded mx-auto w-[500px]"
  >
    <Header />
    <Balance :total="total" />
    <IncomeExpenses :income="+income" :expenses="+expense"/>
    <TransactionList :transactions="transactions" @transactionDeleted="handleTransactionDeleted" />
    <AddTransaction @transactionSubmitted="handleTransactionSubmitted" />
  </main>
</template>
