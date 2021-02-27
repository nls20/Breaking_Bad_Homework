<template>
  <div v-if='character'>
      <h2>{{character.name}}</h2>
          <div>
          <p><span>Nickname</span>: {{character.nickname}}</p>
          <p><span>Birthday</span>: {{character.birthday}}</p>
          <p><span>Occupation</span>: {{character.occupation}}</p>
        </div>
        <div>
          <img :src="character.img" :alt="character.name">
        </div>
  </div>
</template>

<script>
import {eventBus} from '../main.js';

export default {
    name: 'character-detail',
    props: ['character']
}
</script>

<style>

</style>