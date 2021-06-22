<template>
  <div id="app">
    <todoheader></todoheader>
    <todoinput></todoinput>
    <todolist></todolist>
  </div>
</template>

<script>
import Todoheader from './components/todoheader.vue'
import Todoinput from './components/todoinput.vue'
import Todolist from './components/todolist.vue'

export default {
  components: {
    Todoheader,
    Todoinput,
    Todolist,
  }
}
</script>

<style>

</style>
