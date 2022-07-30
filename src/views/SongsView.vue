

<template>
  <div class="songs">
    <SongsList />
  </div>
</template>

<script>
// @ is an alias to /src
import SongsList from '@/components/SongsList.vue'

export default {
  name: 'SongsView',
  components: {
    SongsList
  }
}
</script>