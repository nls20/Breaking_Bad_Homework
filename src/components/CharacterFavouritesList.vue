<template>
<div id="favourites-list">
    <character-header title="FAVOURITE CHARACTERS"></character-header>
    <ul>
    <character-favourites-list-item
    v-for="(character, index) in favourites"
    :character="character"
    :key="index"
    ></character-favourites-list-item>
    </ul>
</div>
</template>

<script>
import CharacterFavouritesListItem from '@/components/CharacterFavouritesListItem';
import CharacterHeader from '@/components/CharacterHeader';

export default {
    props: ["favourites"],
    components: {
        "character-favourites-list-item": CharacterFavouritesListItem,
        "character-header": CharacterHeader
    }
};
</script>

<style>
    ul {
        padding: 20px;
    }


</style>