<template>
  <div id="character-info-container">
    <character-header :title="character.name" />
      <div id="character-info">
        <p>Character Status: {{ character.status }}</p>
        <div>
            <img :src="character.img" :alt="character.name">
        </div>
      </div>
    </div>
</template>

<script>
import CharacterHeader from "@/components/CharacterHeader";

export default {
  props: ["character"],
  components: {
    "character-header": CharacterHeader,
  }
};
</script>

<style scoped>

#character-info-container {
    display: flex;
    flex-direction: column;
    width: 300px;
    height: 500px;
    padding: 20px;
    border-radius: 25px;
    border: 2px solid dodgerblue;
    background-color: aquamarine;
    margin-left: 20px;
    align-items: center;;
    }
</style>