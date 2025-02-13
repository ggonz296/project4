<script setup>
    import {defineProps, defineEmits} from 'vue'

    //Will pass the cart array into this file
    const props = defineProps({
        cart: Array,
    })

    //Creating event to confirm purchase
    const emit = defineEmits(['confirmPurchase'])

    const confirmPurchase = () =>{
        emit('confirmPurchase')
        alert("Thank you!")
    }
</script>

<template>
    
    <button @click="confirmPurchase">Confirm Purchase</button>
    
    <div>
        <h2>Purchase Games: In Cart</h2>
        <ul>
            <li v-for="x in cart" :key="x.id">
                {{ x.title }} - ${{ x.price }}
            </li>
        </ul>
    </div>
    

</template>