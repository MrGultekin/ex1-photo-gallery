<script setup>
// import {defineNuxtComponent} from "nuxt/app";
import {computed, ref} from "vue";
// import {defineProps, computed, ref} from "vue"; import not necessary anymore for defineProps.

defineProps({
  title: {
    type: String,
    default: "Mustafa`s Nuxt",
    // required: true NO NEED TO write this bcoz already default.
  }
})

// export default defineNuxtComponent({
//   data: () => ({
let todoList = ref([])
// }),
// methods: {
function fetchTodoList() {
  fetch('https://jsonplaceholder.typicode.com/todos/')
      .then(response => response.json())
      .then(json => todoList.value = json)
}

// computed: {
const completedTodos = computed(() => {
  return todoList.value.filter(todo => todo.completed)
})

// remainingTodos() {
//   return this.todoList.filter(todo => !todo.completed);
// }
const remainingTodos = computed(() => {
  return todoList.value.filter(todo => !todo.completed);
})

</script>


<template>
  <div class="section">
    <slot name="hero" />


    <!--    <img src="/todo.jpg" alt="Eden Constantino">-->
    <!--    <p>-->
    <!--      Photo by <a-->
    <!--        href="https://unsplash.com/@edenconstantin0?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Eden-->
    <!--      Constantino</a> on <a-->
    <!--        href="https://unsplash.com/s/photos/todos?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>-->
    <!--    </p>-->


    <h1 class="title">{{ title }}</h1>
    <button @click="fetchTodoList"> Click to fetch Data</button>

<!--     Metrics Slot-->
    <slot name="metrics" :completedSayisi="completedTodos"/>

<!--    <p>Total todos :{{ todoList.length }}</p>-->
<!--    <p>Completed todos :{{ completedTodos.length }}</p>-->
<!--    <p>Uncompleted todos :{{ remainingTodos.length }}</p>-->



    <!--    <pre>-->
    <!--      {{todoList}}-->
    <!--    </pre>-->

    <ul :class="$style.list">
      <li v-for="todo in todoList" :key=" `todo-id-${todo.id}` ">
        <input type="checkbox" :checked="todo.completed"/>
        {{ todo.title }}
      </li>
    </ul>
  </div>
</template>

<style module>
.list {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
}
</style>