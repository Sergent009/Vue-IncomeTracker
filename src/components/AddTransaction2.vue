<template>
 
    <h3>Add new transaction</h3>
    <form id="form" @submit.prevent="onSubmit">
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

<script>
import {ref} from 'vue' 
// import useToast from 'vue-toastification'

    export default {
        name: 'AddTransaction2',

        setup(){
            const text = ref('')
            const amount = ref('')

            // const toast = useToast()


            const onSubmit = () => {
                if(!text.value || !amount.value){
                    // toast.error('Both fields should be filled properly.')
                    throw new Error("Both fields should be filled properly")
                }
                text.value = ''
                amount.value = ''
            }

            return{
                onSubmit,
                text,
                amount
            }
        }
    }
</script>

<style scoped>

</style>