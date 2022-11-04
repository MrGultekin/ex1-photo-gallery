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

<template>

  <div class="container">
    <div class="section">
      <div class="columns">
        <div class="column">
          <ToDViewer title="Instead of Mustafa`s Nuxt as prop">
            <template v-slot:hero>
              <h3> SLOT in component and use it HERE </h3>
              <img src="/todo.jpg" alt="todoPic">
            </template>
<!--            <template #metrics="slotProps">-->
<!--            <template v-slot:metrics="slotProps">-->
<!--              <strong> {{slotProps.completedSayisi.length}} </strong>-->
<!--&lt;!&ndash;              <strong>{{slotProps.completed.length}} items completed</strong>&ndash;&gt;-->
<!--              <h3> Helped by v-slot:metrics in tod COMPONENT</h3>-->
<!--            </template>-->
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