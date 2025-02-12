<script setup>
import { defineProps, defineEmits} from 'vue';

const props = defineProps(['games', 'cart']);
const emit = defineEmits(['select-game']);

//This checks whether the game is selected or not
const isInCart = (game) => {
    return props.cart.some(item => item.id === game.id)
}
// Function to emit event when button is clicked
const selectGame = (game) => {
    emit('select-game', game);
}
</script>

<template>
    <!--x is the game in games-->
    <h1>Add a Game</h1>
    <div v-for="x in games" :key="x.id" class="Games">
        <!--This displays the game title and price-->
        <h2>{{ x.title }} - ${{ x.price }}</h2>
        <!--The selectGame function is called when
        the button is clicked and displays the 
        appropriate message on the button-->
        <button @click="selectGame(x)"> 
            {{ isInCart(x) ? "Remove Game" : "Add Game"}}
        </button>
    </div>
</template>