<template lang="html">
  <div >
   <h3>Episode detail:</h3>
    <p>Title: {{episode.title}}</p>
    <p>Director: {{episode.director}}</p>
    <p>Release date: {{episode.release_date}}</p>
    <ul>
      <characters-list v-for="(episode, index) in episodes" :key="index" :episode="episode" ></characters-list>
    </ul>
  </div>
</template>

<script>

import CharactersList from './CharactersList.vue'


export default {
  name: 'episode-detail',
  props: ['episode'],
  components: {
    'characters-list': CharactersList
  }
}


</script>

<style lang="css" scoped>
</style>
