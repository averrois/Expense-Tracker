<template>
  <form class="">
    <h4 class="text-xl font-bold">Add Transaction</h4>
    <div class="space-y-2 w-full mt-4">
      <label
        class="text-lg font-medium leading-none peer-disabled:cursor-not-allowed peer-disabled:opacity-70"
        for="text"
      >
        Text
      </label>
      <input
        class="flex h-10 w-full rounded-md px-3 py-3 text-base ring-offset-background bg-grey-200"
        id="text"
        placeholder="Enter your text"
      />
    </div>
    <div class="space-y-2 w-full mt-4">
      <label
        class="text-lg font-medium leading-none peer-disabled:cursor-not-allowed peer-disabled:opacity-70"
        for="amount"
      >
        Amount
        <br />
        <span class="text-base">(positive - income, negative - expense)</span>
      </label>
      <input
        class="flex h-10 w-full rounded-md px-3 py-3 text-base ring-offset-background bg-grey-200"
        id="amount"
        placeholder="Enter your amount"
      />
    </div>
    <button
      type="submit"
      class="mt-4 mb-4 bg-white w-full p-2 text-black font-bold text-lg rounded"
    >
      Submit
    </button>
  </form>
</template>
