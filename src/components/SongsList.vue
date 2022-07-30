<template>
  <div class="songs">
    <h1>{{ title }}</h1>
   
   <div class="wrapper"> <div class="search-filter">
    <!-- use .lazy on the v-model to generate the search term on blur instead of on input. -->
    <label for="searchInput">Search</label>
    <input id="searchInput" class="text-input" v-model.lazy="term" placeholder="search by song title or artist" @keyup.enter="search(term)"/> 
    <h3>You searched for: {{ term }}</h3>

    <h3>Filters</h3>
    <div v-for="filter in filters" :key="filter">
      <!--input type="checkbox" v-model="checkbox" /-->
      <p @click="() => filterSongs(filter)"> {{ filter }} </p>
    </div>
  </div>
      <div class="song-list" >
      <div v-for="song in songs" :key="songs.songtitle">
       <h4>Artist: {{ song.artist }}</h4>
       <p>Song Title: {{ song.songtitle }}</p>
      </div>
    </div>
  </div>
  </div>
</template>

<script>
  const filters = [
     'All',
     'Rob Berrones',
     'MCST',
     'Reel Big Fish',
     'Arms Akimbo'
  ]
  import SongList from '../songs.json'
  

export default {
  name: 'SongsView',
  

  data() {
    return {
      title: "Search For Songs on this page.",
      term: '',
      songs: SongList,
      filters
    }
  },
  methods: {
    /*Need to refactor to use checkboxes not click event and all*/
    filterSongs (artistName) {
      //console.log("clicked")
      this.resetSongs()
      if(artistName !== 'All') {
        this.songs = this.songs.filter((songs) => {
          return songs.artist === artistName
        })
      }
    },
    search(term) {
      //console.log("entered search term")
      this.resetSongs()
      this.songs = this.songs.filter((song)=>{
        return song.songtitle.toLowerCase().includes(term.toLowerCase())
      })
    },
    resetSongs() {
      this.songs = SongList
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
  min-width: 200px;
}
.wrapper {
  display: flex;
}
.search-filter {
  width: 20%;
  flaot:left;
}
.song-list {
  width: 69%;
  float: right;
  clear: left;
}
</style>
