<script setup>
  import Header from './components/Header.vue';
  import TotalGames from './components/TotalGames.vue';
  import AddGames from './components/AddGames.vue';
  import {ref, computed} from 'vue'

  //My array of games - These are pre-initalized
  const myGames = ref([
    {id: 1, title: "Older Rings", price: 60},
    {id: 2, title: "Monsters", price: 40},
    {id: 3, title: "DC Rivals", price: 50},
  ])

  //My array of items in a cart
  const cart = ref([])

</script>

<template>
  <Header></Header>
  <AddGames :games="myGames" :cart="cart" @select-game="selectGame"></AddGames>
  <TotalGames :total="totalPrice"></TotalGames>
</template>