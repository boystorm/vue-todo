<template>
  <div id="app">
    <todoheader></todoheader>
    <todoinput></todoinput>
    <todolist></todolist>
    <todofooter></todofooter>
  </div>
</template>

<script>
import Todoheader from './components/todoheader.vue'
import Todoinput from './components/todoinput.vue'
import Todolist from './components/todolist.vue'
import Todofooter from './components/todoFooter.vue'

export default {
  components: {
    Todoheader,
    Todoinput,
    Todolist,
    Todofooter
  }
}
</script>

<style>

</style>
