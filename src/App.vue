<template>
  <div id="app">
    <h1>Star Wars</h1>
    <h2>Choose you episode for details</h2>
    <div class="main-container">
      <episode-list :episodes="episodes"></episode-list>
      <episode-detail v-if="selectedEpisode" :character="selectedEpisode" :episode="selectedEpisode"></episode-detail>
    </div>
  </div>
</template>

<script>

import CharactersList from '@/components/CharactersList.vue';
import AppHeader from '@/components/AppHeader.vue';
import EpisodeDetail from '@/components/EpisodeDetail.vue';
import EpisodeList from '@/components/EpisodeList.vue';
import {eventBus} from '@/main.js';

export default {
  name: 'App',
  data() {
    return{
      episodes: [],
      characters: [],
      selectedEpisode: null,
      selectedCharacter: null

    }
  },
  mounted(){
    fetch("https://swapi.dev/api/films/")
    .then(res => res.json())
    .then(data => this.episodes = data.results)

    eventBus.$on('episode-selected', (episode) => {
      this.selectedEpisode = episode;
    })
  },
  methods: {
      },
  components: {
    'episode-list': EpisodeList,
    'episode-detail': EpisodeDetail,
    'app-header': AppHeader,

  }

}
</script>

<style>
.main-container {
  display: flex;
  justify-content: space-between;
}
</style>
