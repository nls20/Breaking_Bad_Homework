<template>
  <div id="app">
    <h1>BREAKING BAD</h1>
    <div id="list-info" v-if="characters.length">
      <character-list :characters='characters'></character-list>
      <character-info
      v-if="selectedCharacter"
      :character="selectedCharacter"
      ></character-info>
    </div>
    <character-favourites-list :favourites="favourites"></character-favourites-list>
  </div>


</template>

<script>
import { eventBus } from './main.js';

import CharacterList from './components/CharacterList.vue';
import CharacterHeader from './components/CharacterHeader';
import CharacterFavouritesList from './components/CharacterFavouritesList';
import CharacterInfo from './components/CharacterInfo';

export default {
  name: 'app',
  data() {
    return {
      characters: [],
      selectedCharacter: null
    };
  },
  computed: {
    favourites: function () {
      return this.characters.filter(character => character.isFavourite);
    }
  },
  methods: {
    getCharacters: function() {
      fetch("https://breakingbadapi.com/api/characters")
     .then(res => res.json())
     .then(characterData => {
       characterData.forEach(character => (character.isFavourite = false));
       this.characters = characterData;
    })
    .then(() => this.sortCharacters("name"));
  },
    sortCharacters: function (property) {
      this.characters.sort((a, b) => {
        return a[property] < b[property] ? -1 : 1;
    });
  },
    markFavourite: function(character) {
      const index = this.characters.indexOf(character);
      this.characters[index].isFavourite = true;
  }
  },
  components: {
    'character-header': CharacterHeader,
    'character-list': CharacterList,
    'character-favourites-list': CharacterFavouritesList,
    'character-info': CharacterInfo
  },
  mounted() {
    this.getCharacters();

    eventBus.$on('character-selected', character => {this.selectedCharacter = character});
    
    eventBus.$on("favourite-added", character => this.markFavourite(character));
  },
}
</script>

<style>

h1 {
  color: white;
  text-align: center;
  font-size: 40px;
}
#app {
  background-image: url('https://f3e6t7k9.stackpathcdn.com/wp-content/uploads/2015/05/Breaking-Bad-RV.png');
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  background-attachment: fixed;
}

#list-info {
  display: flex;

}
</style>
