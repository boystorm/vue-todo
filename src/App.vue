<template>
  <div id="app">
    <todoheader></todoheader>
    <todoinput v-on:todoList="todoList"></todoinput>
    <todolist v-bind:propsdata="todoLists"></todolist>
    <todofooter></todofooter>
  </div>
</template>

<script>
import Todoheader from './components/todoheader.vue'
import Todoinput from './components/todoinput.vue'
import Todolist from './components/todolist.vue'
import Todofooter from './components/todoFooter.vue'

export default {
  // 할일을 상위 컴포넌트에서 작업 후 props로 전달
  data (){
    return {
      todoLists: []
    }
  },
  methods: {
    todoList(message) {
      // 로컬스토리지에 담는 로직
      localStorage.setItem(message, message);
      this.todoLists.push(message);
    }
  },
  created() {
      if(localStorage.length > 0){
          for(let i = 0; i < localStorage.length ; i++) {
              if((localStorage.key(i) != 'loglevel:webpack-dev-server') && (localStorage.key(i) != '')){
                  this.todoLists.push(localStorage.key(i));
              }
          }
      }
  },
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
