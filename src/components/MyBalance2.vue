<template>
   
    <h4>Your Balance</h4>
    <h1 id="balance">${{ total }}</h1>

</template>

<script>
    export default {
        name: 'MyBalance2',
        props: ['total']
    }
</script>

<style scoped>

</style>