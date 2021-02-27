<template>
  <div>
    <h1>Characters</h1>
    <div>
      <characters-list :characters='characters'></characters-list>
      <character-detail :character="selectedCharacter"></character-detail>
    </div>
  </div>


</template>

<script>

import CharacterDetail from './components/CharacterDetail.vue';
import CharactersList from './components/CharactersList.vue';
import { eventBus } from './main.js';

export default {
  name: 'app',
  data() {
    return {
      characters: [],
      selectedCharacter: null
    };
  },
  components: {
    'character-detail': CharacterDetail,
    'characters-list': CharactersList
  },
  mounted() {
    fetch("https://breakingbadapi.com/api/characters")
    .then(res => res.json())
    .then(characters => this.characters = characters)

    eventBus.$on('character-selected', (character) => {
    this.selectedCharacter = character
      })
  },
}
</script>

<style>

</style>
