<script setup>
    import { ref, defineProps} from 'vue';

    const props = defineProps(['cart']);

    const userMoney = ref('')
</script>

<template>
    <form @submit.prevent="confirmPurchase">
        <label>Enter Amount</label>
        <input type="number" v-model="userMoney" placeholder="Enter Amount">
        <button type="submit">Confirm Purchase</button>
    </form>
    
    

</template>