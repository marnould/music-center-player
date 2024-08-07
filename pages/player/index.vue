<template>
  <div>
    <player />
  </div>
</template>
<script>
import player from '@/components/player/player'
export default {
  components: {
    player
  }
}
</script>

tracks = [];
tracksLoading: false,


async getTracks() {
this.tracksLoading = true
try {
let data = await this.$axios.$get('/tracks')
this.tracks = data
this.tracksLoading = false
} catch (err) {
this.tracksLoading = false
swal('Error', 'Error Fetching Tracks', 'error')
}
}

created() {
this.getTracks()
}
