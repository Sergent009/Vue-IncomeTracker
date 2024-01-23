<template>

<MyHeader2 />
<div class="container">
  <MyBalance2 :total="total" />
  <IncomeExpense2 :income="income" :expense="expense" />
  <TransactionList2 :transactions="transactions" />
  <AddTransaction2 />
</div>


</template>

<script>
import MyHeader2 from './components/MyHeader2.vue'
import MyBalance2 from './components/MyBalance2.vue'
import IncomeExpense2 from './components/IncomeExpense2.vue'
import TransactionList2 from './components/TransactionList2.vue'
import AddTransaction2 from './components/AddTransaction2.vue'
import { ref, computed } from 'vue'

export default {
  name: 'App',
  components: {
    MyHeader2,
    MyBalance2,
    IncomeExpense2,
    TransactionList2,
    AddTransaction2
  },
  setup(){
    const transactions = ref([
      {id: 1, text: 'Flower', amount: -19.99},
      {id: 2, text: 'Salary', amount: 299.97},
      {id: 3, text: 'Book', amount: -10},
      {id: 4, text: 'Camera', amount: 150},
      ])

      // get total balance
      const total = computed(() => {
        return transactions.value.reduce((acc, transaction) =>{
        return acc + transaction.amount
        }, 0)
      })

      // get income
      const income = computed(() => {
        return transactions.value.filter((transaction) => transaction.amount > 0).reduce((acc, transaction) => {
          return acc + transaction.amount
        }, 0).toFixed(2)
      })

      // get expense
      const expense = computed(() => {
        return transactions.value.filter((transaction) => transaction.amount < 0).reduce((acc, transaction) =>{
          return acc + transaction.amount
        }, 0).toFixed(2)
      })

      return{
        transactions,
        total,
        income,
        expense
      }
    }
}
</script>

<style>

@import url('https://fonts.googleapis.com/css?family=Lato&display=swap');

:root {
  --box-shadow: 0 1px 3px rgba(0, 0, 0, 0.12), 0 1px 2px rgba(0, 0, 0, 0.24);
}

* {
  box-sizing: border-box;
}

body {
  background-color: #f7f7f7;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  margin: 0;
  font-family: 'Lato', sans-serif;
  font-size: 18px;
}

.container {
  margin: 30px auto;
  width: 400px;
}

h1 {
  letter-spacing: 1px;
  margin: 0;
}

h3 {
  border-bottom: 1px solid #bbb;
  padding-bottom: 10px;
  margin: 40px 0 10px;
}

h4 {
  margin: 0;
  text-transform: uppercase;
}

.inc-exp-container {
  background-color: #fff;
  box-shadow: var(--box-shadow);
  padding: 20px;
  display: flex;
  justify-content: space-between;
  margin: 20px 0;
}

.inc-exp-container > div {
  flex: 1;
  text-align: center;
}

.inc-exp-container > div:first-of-type {
  border-right: 1px solid #dedede;
}

.money {
  font-size: 20px;
  letter-spacing: 1px;
  margin: 5px 0;
}

.money.plus {
  color: #2ecc71;
}

.money.minus {
  color: #c0392b;
}

label {
  display: inline-block;
  margin: 10px 0;
}

input[type='text'],
input[type='number'] {
  border: 1px solid #dedede;
  border-radius: 2px;
  display: block;
  font-size: 16px;
  padding: 10px;
  width: 100%;
}

.btn {
  cursor: pointer;
  background-color: #9c88ff;
  box-shadow: var(--box-shadow);
  color: #fff;
  border: 0;
  display: block;
  font-size: 16px;
  margin: 10px 0 30px;
  padding: 10px;
  width: 100%;
}

.btn:focus,
.delete-btn:focus {
  outline: 0;
}

.list {
  list-style-type: none;
  padding: 0;
  margin-bottom: 40px;
}

.list li {
  background-color: #fff;
  box-shadow: var(--box-shadow);
  color: #333;
  display: flex;
  justify-content: space-between;
  position: relative;
  padding: 10px;
  margin: 10px 0;
}

.list li.plus {
  border-right: 5px solid #2ecc71;
}

.list li.minus {
  border-right: 5px solid #c0392b;
}

.delete-btn {
  cursor: pointer;
  background-color: #e74c3c;
  border: 0;
  color: #fff;
  font-size: 20px;
  line-height: 20px;
  padding: 2px 5px;
  position: absolute;
  top: 50%;
  left: 0;
  transform: translate(-100%, -50%);
  opacity: 0;
  transition: opacity 0.3s ease;
}

.list li:hover .delete-btn {
  opacity: 1;
}

</style>
