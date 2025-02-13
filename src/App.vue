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
      //Add game if not in cart
      cart.value.push(game) 
    } else {
      //Remove Game from cart
      cart.value.splice(x, 1)
    }
}

//This will compute the price total/sum 
const totalPrice = computed(() =>{
  return cart.value
  .reduce((total, game) => {
    return total+game.price
  }, 0)
})

//This will clear the cart after purchase
const confirmPurchase = () =>{
  cart.value = [];
}
</script>

<template>
  <Header></Header>
  <AddGames :games="myGames" :cart="cart" @select-game="selectGame"></AddGames>
  <TotalGames :total="totalPrice"></TotalGames>
  <PurchaseGames :cart="cart" @confirmPurchase="confirmPurchase"></PurchaseGames>
</template>