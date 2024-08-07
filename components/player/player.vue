<template>
  <section class="mt-5">
    <table class="table">
      <thead>
      <tr>
        <th scope="col">#</th>
        <th scope="col">Title</th>
        <th scope="col">Artist</th>
        <th scope="col">Date created</th>
        <th scope="col">Action</th>
      </tr>
      </thead>
      <div
        v-if="tracksLoading"
        class="spinner-border"
        style="width: 3rem; height: 3rem;"
        role="status"
      >
        <span class="sr-only">Loading...</span>
      </div>
      <tbody v-else>
      <tr v-for="(track, index) in tracks" :key="index">
        <td>{{ index + 1 }}</td>
        <td>{{ track.title }}</td>
        <td>{{ track.artist }}</td>
        <td>{{ track.created }}</td>
        <td>
          <button class="btn btn-info" @click="deleteTrack(track._id)">Delete</button>
        </td>
      </tr>
      </tbody>
    </table>

  </section>
</template>
