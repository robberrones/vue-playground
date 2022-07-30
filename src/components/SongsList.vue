<template>
  <div class="songs">
    <h1>{{ title }}</h1>
    <!-- use .lazy on the v-model to generate the search term on blur instead of on input. -->
    <input class="text-input" v-model.lazy="searchTerm" placeholder="search by song title or artist" /> 
    <h3>You searched for: {{ searchTerm }}</h3>

    <h3>Filters</h3>
    <div v-for="filter in filters">
      <input type="checkbox" v-model="checkbox" />
      <label> {{ filter }} </label>
    </div>
      <div v-for="song in songs">
       <h4>Artist: {{ song.artist }}</h4>
       <p>Song Title: {{ song.songtitle }}</p>
      </div>
    
  </div>
</template>

<script>
  import SongList from '../songs.json'
  const filters = [
     'Rob Berrones',
     'MCTS',
     'Reel Big Fish',
     'Arms Akimbo'
  ]
export default {
  name: 'SongsView',
  data() {
    return {
      title: "Search For Songs on this page.",
      searchTerm: '',
      songs: SongList,
      filters 
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
input.text-input {
  padding:  8px;
  font-size: 16px;
  line-height:  1.5;
  min-width: 300px;
}
</style>
