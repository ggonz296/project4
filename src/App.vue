<script setup>
  import Header from './components/Header.vue';
  import TotalGames from './components/TotalGames.vue';
  import AddGames from './components/AddGames.vue';
  import PurchaseGames from './components/PurchaseGames.vue';
  import {ref, computed} from 'vue'

  //My array of games - These are pre-initalized
  const myGames = ref([
    {id: 1, title: "Older Rings", price: 60},
    {id: 2, title: "Monsters", price: 40},
    {id: 3, title: "DC Rivals", price: 50},
  ])

  //My array of items in a cart
  const cart = ref([])

  //This will add or remove games from cart
  const selectGame = (game) => {
    const x = cart.value.findIndex(item => item.id === game.id)
    if (x === -1) {
      cart.value.push(game) // Add game if not in cart
    } else {
      cart.value.splice(x, 1) // Remove game if already in cart
  }
}

//This will compute the price total/sum 
const totalPrice = computed(() =>{
  return cart.value
  .reduce((total, game) => {
    return total+game.price
  }, 0)
})
</script>

<template>
  <Header></Header>
  <AddGames :games="myGames" :cart="cart" @select-game="selectGame"></AddGames>
  <TotalGames :total="totalPrice"></TotalGames>
  <PurchaseGames :cart="cart"></PurchaseGames>
</template>