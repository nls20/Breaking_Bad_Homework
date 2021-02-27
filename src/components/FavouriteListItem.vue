<template>
  <div id="favourite_characters">
      <h2>Favourite Characters</h2>
      <ul>
          <li :v-for="favouriteCharacter in favouriteCharacters">{{ favouriteCharacter.name }}
              
          </li>
      </ul>

  </div>
</template>

<script>
export default {
    name: 'favourite-characters',
    props: ['favouriteCharacters']
}
</script>

<style>

</style>