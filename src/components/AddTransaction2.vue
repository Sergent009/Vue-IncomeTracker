<template>
    <h3>Add new transaction</h3>
    <form  :class="{ 'errorAnimation': animation }"  id="form" @submit.prevent="onSubmit">

        <div class="form-control">
            <label for="text">Text</label>
            <input type="text" v-model="text" id="text" placeholder="Enter text...">
        </div>

        <div class="form-control">
            <label for="amount">Amount<br />(negative - expense, positive - income)</label>
            <input type="text" id="amount" v-model="amount" placeholder="Enter Amount...">
        </div>

        <button class="btn">Add transaction</button>
    </form>

</template>

<script setup>
import {ref, defineEmits} from 'vue' 


            const animation = ref(false)
            const text = ref('')
            const amount = ref('')

            const emit = defineEmits(['transactionSubmitted'])


            const onSubmit = () => {
                if(!text.value || !amount.value){
                    animation.value = true

                    setTimeout(() => {
                        animation.value = false
                    }, 2000)
                }

            const transactionData = {
                text: text.value,
                amount: parseFloat(amount.value)
            }

            emit('transactionSubmitted', transactionData)

                text.value = ''
                amount.value = ''
            }

</script>

<style scoped>

.errorAnimation {
  animation: shake 1s ease-in-out; /* Use your preferred animation duration and easing */
  background-color: rgba(255, 0, 0, 0.3); 
  border: 2px solid red; 
  border-radius: 5px; 
}

@keyframes shake {
  0%, 100% {
    transform: translateX(0);
  }
  25%, 75% {
    transform: translateX(-20px);
  }
  50% {
    transform: translateX(20px);
  }
}

</style>