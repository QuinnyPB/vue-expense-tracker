<template>
  <h3>History</h3>
  <ul id="list" class="list">
    <!-- DUMMY DATA -->
    <!-- <li class="minus">
      Cash <span>-$400</span><button class="delete-btn">x</button>
    </li>
    <li class="plus">
      Paycheck <span>$850</span><button class="delete-btn">x</button>
    </li> -->

    <!-- OPTIONS API -->
    <li
      v-for="transaction in transactions"
      v-bind:key="transaction.id"
      :class="transaction.amount < 0 ? 'minus' : 'plus'"
    >
      {{ transaction.text }} <span>${{ transaction.amount }}</span
      ><button @click="deleteTransaction(transaction.id)" class="delete-btn">
        x
      </button>
    </li>

    <!-- COMPOSITION API -->
  </ul>
</template>

<script setup>
import { defineProps } from "vue";

const emit = defineEmits(["transactionDeleted"]);

const props = defineProps({
  transactions: {
    type: Array,
    required: true,
  },
});

const deleteTransaction = (id) => {
  emit("transactionDeleted", id);
};

// moved to global state
// const transactions = [
//   { id: 1, text: "Flower", amount: -19.99 },
//   { id: 2, text: "Salary", amount: 299.97 },
//   { id: 3, text: "Book", amount: -10 },
//   { id: 4, text: "Camera", amount: 150 },
// ];

// COMPOSITION API
// without 'setup' in script tag
// export default {
//   setup() {
//     const transactions = [
//       { id: 1, text: "Flower", amount: -19.99 },
//       { id: 2, text: "Salary", amount: 299.97 },
//       { id: 3, text: "Book", amount: -10 },
//       { id: 4, text: "Camera", amount: 150 },
//     ];

//     return {
//       transactions,
//     };
//   },
// };

// OPTIONS API
// export default {
//   data() {
//     return {
//       transactions: [
//         { id: 1, text: "Flower", amount: -19.99 },
//         { id: 2, text: "Salary", amount: 299.97 },
//         { id: 3, text: "Book", amount: -10 },
//         { id: 4, text: "Camera", amount: 150 },
//       ],
//     };
//   },
// };
</script>
