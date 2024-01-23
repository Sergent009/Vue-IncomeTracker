<template>
  <h3>History</h3>
  <ul id="list" class="list">
    <li v-for="transaction in transactions" :key="transaction.id"
    :class="transaction.amount < 0 ? 'minus' : 'plus'">
        {{ transaction.text }} <span>${{ transaction.amount }}</span>
        <button class="delete-btn">x</button>
    </li>
  </ul>
</template>

<script>
import {defineProps} from 'vue'

    export default {
        name: 'TransactionList2',

       setup(){
        const props = defineProps({
            transactions: {
                type:Array,
                required: true
            }
        })

        return{
            props
        }
       }
    }
</script>

<style scoped>

</style>