<template>
  <div class="character-list-item" v-if="characters.length">
          <character-list-item v-for="(character, index) in characters" 
          :character="character" 
          :key="index">
          </character-list-item>
          </div>
</template>

<script>
import CharacterListItem from '@/components/CharacterListItem';

export default {
    name: 'character-list',
    props: ['characters'],
    components: {
        "character-list-item": CharacterListItem
    }
};
</script>

<style>
.character-list-item {
    width: 60%;
    height: 550px;
    overflow-y: scroll;
    display: flex;
    flex-wrap: wrap;
}
</style>