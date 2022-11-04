<!--<script setup>-->
<!--// import {defineNuxtComponent} from '#app'-->
<!--// compositional API does not need this import-->

<!--import {computed, ref, reactive} from 'vue'-->
<!--import ToDViewer  from './components/ToDViewer'-->

<!--let photoGallery = ref([])-->


<!--const numberOfPhotos = computed(() => {-->
<!--  return photoGallery.value.length;-->
<!--})-->

<!--const evenAlbums = computed(() => {-->
<!--  return photoGallery.value.filter(item => item.albumId % 2 === 0)-->
<!--})-->
<!--const oddAlbums = computed(() => {-->
<!--  return photoGallery.value.filter(item => item.albumId % 2 === 1)-->
<!--})-->


<!--function fetchPhotoGallery() {-->
<!--  fetch('https://jsonplaceholder.typicode.com/photos')-->
<!--      .then(response => response.json())-->
<!--      .then(json => {-->
<!--        photoGallery.value = json-->
<!--      })-->
<!--}-->

<!--</script>-->

<script setup>
import PhotoGallery from './components/photoGallery.vue'
import ToDViewer from './components/toDViewer.vue'
</script>

<template>

  <div class="container">
    <div class="section">
      <div class="columns">
        <div class="column">
          <ToDViewer title="Instead of Mustafa`s Nuxt as prop">
            <h2> SLOT in component and use it HERE</h2>
            <img src="/todo.jpg" alt="todoPic">
          </ToDViewer>
        </div>
        <div class="column">
          <PhotoGallery/>
        </div>
      </div>
    </div>
  </div>

</template>

<style lang="scss">
@import './node_modules/bulma/bulma.sass';

.list {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
}
</style>