<template>
  <div id="selected_character">
      <h2>{{selectedCharacter.name}}</h2>
      <img class="img" :src="selectedCharacter.img" />
  </div>
</template>

<script>
export default {
    name: "character-detail",
    props: ["selectedCharacter"]
}
</script>

<style>

</style>