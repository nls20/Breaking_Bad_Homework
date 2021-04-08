<template>
<div class="characterlistitem">
  <p>{{ character.name }}</p>
  <img :src="character.img" :alt="character.name">
  <button v-on:click="displayInfo">Click for Info</button>
  <button v-on:click="addFavourite">Add to Favourites</button>
  </div>
</template>

<script>
import {eventBus} from '@/main.js';

export default {
    name: 'character-list-item',
    props: ['character'],
    methods: {
        displayInfo: function () {
            eventBus.$emit('character-selected', this.character)
        },

        addFavourite: function () {
            eventBus.$emit('favourite-added', this.character)
        }
    }
};
</script>


<style>

p {
  font-size: 25px;
  color: black;
}

.characterlistitem {
  display: flex;
  flex-direction: column;
  padding: 30px;
  align-items: center;
  width: 200px;
  height: 380px;
  border-radius: 25px;
  border: 2px solid dodgerblue;
  background-color: lightblue;
}

button {
    padding: 10px;
    font-size: 20px;
    text-decoration: none;
    background-color: aquamarine;
    color: white;
}

img {
    height: 150px;
    width: 150px;
    padding: 30px;
}
    </style>