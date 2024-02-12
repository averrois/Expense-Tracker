<script setup lang="ts">
import type { TransactionProps } from "@/components/types"
import { computed, ref, onMounted } from "vue"
import Header from "@/components/Header.vue"
import Balance from "@/components/Balance.vue"
import IncomeExpenses from "@/components/IncomeExpenses.vue"
import TransactionList from "@/components/TransactionList.vue"
import AddTransaction from "@/components/AddTransaction.vue"
import { useToast } from "vue-toastification"

defineProps<{
  transactions?: TransactionProps[]
}>()

const toast = useToast()

const transactions = ref<TransactionProps[]>([])

onMounted(() => {
  const savedTransactions = localStorage.getItem("transactions")

  if (savedTransactions) {
    transactions.value = JSON.parse(savedTransactions)
  }
})

const total = computed(() => {
  return transactions.value.reduce((acc, transaction) => {
    return acc + transaction.amount
  }, 0)
})

// Get income
const income = computed(() => {
  return transactions.value
    .filter((transaction) => transaction.amount > 0)
    .reduce((acc, transaction) => {
      return acc + transaction.amount
    }, 0)
    .toFixed(2)
})

const expense = computed(() => {
  return (
    transactions.value
      .filter((transaction) => transaction.amount < 0)
      .reduce((acc, transaction) => {
        return acc + transaction.amount
      }, 0) * -(1).toFixed(2)
  )
})

const generateUniqueId = () => {
  return Math.floor(Math.random() * 1000000000)
}

// Add transaction
const handleTransactionSubmitted = (transactionData: any) => {
  transactions.value.push({
    id: generateUniqueId(),
    ...transactionData,
  })

  saveTransactionToLocalStorage()

  toast.success("Transaction added successfully")
}

// Delete Transaction
const handleTransactionDeleted = (id: number) => {
  transactions.value = transactions.value.filter((transaction) => transaction.id !== id)

  saveTransactionToLocalStorage()

  toast.success("Transaction deleted successfully")
}

// Save Transaction
const saveTransactionToLocalStorage = () => {
  localStorage.setItem("transactions", JSON.stringify(transactions.value))
}
</script>

<template>
  <main class="border-[2px] text-left max-sm:w-full border-grey-200 bg-grey-100 px-6 py-2 rounded mx-auto w-[500px]">
    <Header />
    <Balance :total="total" />
    <IncomeExpenses :income="+income" :expenses="+expense" />
    <TransactionList :transactions="transactions" @transactionDeleted="handleTransactionDeleted" />
    <AddTransaction @transactionSubmitted="handleTransactionSubmitted" />
  </main>
</template>
