<template>
  <div id="app">
    <label for="character_select">Select a Character:</label>
    <select id="character_select" v-model="selectedCharacter">
      <option disabled value="">Select a Character</option>
      <option v-for="character in characters" :key="character" :value="character">{{character.name}}</option>
    </select>

    <character-detail v-if="selectedCharacter" :selectedCharacter="selectedCharacter"></character-detail>

    <button v-if="!favouriteCharacters.includes(selectedCharacter)" v-on:click="addToFavourites">Add Character</button>

    <favourite-characters :favouriteCharacters="favouriteCharacters"></favourite-characters>
  </div>


</template>

<script>

import CharacterDetail from './components/CharacterDetail.vue';
import FavouriteListItem from './components/FavouriteListItem.vue';

export default {
  name: 'App',
  data() {
    return {
      characters: [],
      selectedCharacter: null,
      favouriteCharacters: []
    }
  },
  components: {
    'character-detail': CharacterDetail,
    'favourite-characters': FavouriteListItem
  },
  mounted() {
    this.getCharacters()
  },
  methods: {
    getCharacters: function () {
      fetch("https://breakingbadapi.com/api/characters")
      .then(res => res.json())
      .then(characters => this.characters = characters)
    },
    addToFavourites: function() {
      this.favouriteCharacters.push(this.selectedCharacter)
    }
  }
}
</script>

<style>

</style>
