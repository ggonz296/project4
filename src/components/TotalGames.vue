<script setup>
    import{defineProps} from 'vue'
    const props = defineProps({
        total:{
            type: Number,
            required: true,
        }
    })
</script>

<template>
    <h2>Total Price: ${{ total }}</h2>
</template>