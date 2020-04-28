<template lang="html">
  <div >

  <label for="characters-list">Characters List</label>
  <ul>

  </ul>
  <p> {{episode.characters}}</p>
  </div>
</template>

<script>
export default {
  name: 'characters-list',
  props: ['episode'],
  data(){
    return{
      episodes: []
    }
  },
  mounted() {
    this.getEpisodes()
  },
  watch: {
    character: function(){
      this.getEpisodes()
    }
  },
  methods:{
    getEpisodes(){
      const episodePromises = this.episode.characters.map((episode) => {
        return fetch(episode).then(res => res.json());
      })
      Promise.all(episodePromises)
      .then((data) => {
        this.episodes = data;
      })
    }
  }
}

</script>

<style lang="css" scoped>
</style>
