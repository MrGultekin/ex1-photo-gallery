<script setup>
// import {defineNuxtComponent} from '#app'
// compositional API does not need this import

import {computed, ref, reactive} from 'vue'
import ToDViewer  from './components/ToDViewer'

let photoGallery = ref([])


const numberOfPhotos = computed(() => {
  return photoGallery.value.length;
})

const evenAlbums = computed(() => {
  return photoGallery.value.filter(item => item.albumId % 2 === 0)
})
const oddAlbums = computed(() => {
  return photoGallery.value.filter(item => item.albumId % 2 === 1)
})


function fetchPhotoGallery() {
  fetch('https://jsonplaceholder.typicode.com/photos')
      .then(response => response.json())
      .then(json => {
        photoGallery.value = json
      })
}

</script>

<template>

  <div class="container">
    <div class="section">
      <div class="columns">
        <div class="column">
          <h1>Photo Gallery</h1>
          <button @click="fetchPhotoGallery">Fetch Photos</button>
          <p> Total: {{ numberOfPhotos }} photos are available. </p>
          <p> Even: {{ evenAlbums.length }} photos are available. </p>
          <p> Odd: {{ oddAlbums.length }} photos are available. </p>
          <ul class="list">
            <li v-for="photo in photoGallery" :key=" `photo-id-${photo.id}` ">
              <img :src="photo.thumbnailUrl" alt="colored photos">
            </li>
          </ul>
        </div>

        <div class="column">
          <ToDViewer/>
        </div>
      </div>
    </div>
  </div>


</template>

<style lang="scss">
@import './node_modules/bulma/bulma.sass';
.list{
  display: grid;
  grid-template-columns: repeat(5, 1fr);
}
</style>