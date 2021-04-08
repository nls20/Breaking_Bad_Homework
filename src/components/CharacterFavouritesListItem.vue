<template>
<div class="characterfavitem">
 <p>{{character.name}} </p>
<button v-on:click="selectCharacter">Display Info</button></li>
</div>
</template>

<script>
import {eventBus} from '../main.js'

export default {
    props: ["character"],
    methods: {
        selectCharacter: function () {
            eventBus.$emit("character-selected", this.character);
        }
    }
};
</script>

<style>
   .characterfavitem {
        display: flex;
        flex-direction: column;
        padding: 20px;
        align-items: right;
        width: 150px;
        height: 150px;
        border-radius: 25px;
        border: 6px solid dodgerblue;
        background-color: white;
        margin-left: 20px;
}
</style>