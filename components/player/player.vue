<template>
  <section class="mt-5">
    <table class="table">
      <thead>
      <tr>
        <th scope="col">#</th>
        <th scope="col">Title</th>
        <th scope="col">Artist</th>
        <th scope="col">Album</th>
        <th scope="col">Source</th>
        <th scope="col">Date created</th>
        <th scope="col">Action</th>
      </tr>
      </thead>
      <div
        v-if="trackLoading"
        class="spinner-border"
        style="width: 3rem; height: 3rem;"
        role="status"
      >
        <span class="sr-only">Loading...</span>
      </div>
      <tbody v-else>
      <tr v-for="(track, index) in allTracks" :key="index">
        <td>{{ index + 1 }}</td>
        <td>{{ track.title }}</td>
        <td>{{ track.album ?? "No album" }}</td>
        <td>{{ track.artist ?? "No artist" }}</td>
        <td>{{ track.source }}</td>
        <td>{{ track.createdDate }}</td>
        <td>
          <button class="btn btn-info" @click="deleteTrack(track._id)">Delete</button>
        </td>
      </tr>
      </tbody>
    </table>

  </section>
</template>

<script>
export default {
  data() {
    return {
      allTracks: [],
      trackLoading: false,
    }
  },

  methods: {
    async getAllTracks() {
      this.musicLoading = true
      try {
        this.allTracks = await this.$axios.$get('/track')
        this.trackLoading = false
      } catch (err) {
        this.trackLoading = false
      }
    }
  },

  created() {
    this.getAllTracks()
  }
}
</script>
