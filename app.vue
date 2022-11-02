<script>
import {defineNuxtComponent} from '#app'

export default defineNuxtComponent({

  data: () => ({
    photoGallery: []
  }),
  methods: {
    fetchPhotoGallery() {
      fetch('https://jsonplaceholder.typicode.com/photos')
          .then(response => response.json())
          .then(json => {
            this.photoGallery = json
          })
    }
  }
})
</script>

<template>
  <div>
    <h1>Photo Gallery</h1>

    <button @click="fetchPhotoGallery">Fetch Photos</button>
    <ul>
      <li v-for="photo in photoGallery" :key=" `photo-id-${photo.id}` ">
        <img :src="photo.thumbnailUrl" alt="colored photos">
      </li>

    </ul>
  </div>
</template>

<style></style>