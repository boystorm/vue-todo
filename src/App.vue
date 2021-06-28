<template>
  <div id="app">
    <todoheader></todoheader>
    <todoinput v-on:todoList="todoList"></todoinput>
    <todolist 
        v-bind:propsdata="todoLists" 
        v-bind:showModal="showModal" 
        v-bind:showModalMod="showModalMod" 
        v-bind:message="message"
        v-bind:number="number"
        v-on:showModalExist="showModalExist" 
        v-on:showModalClose="showModalClose"
        v-on:todoModPop="todoModPop">
    </todolist>
    <todofooter v-on:clearAll="clearAll"></todofooter>
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
      todoLists: [],
      showModal: '',
      showModalMod: '',
      message: '',
      number: ''
    }
  },
  methods: {
    todoList(message) {
      // 로컬스토리지에 담는 로직
      for(let i = 0; i <= localStorage.length; i++){
        if(localStorage.key(i) == message){
          this.showModal = !this.showModal;
          
          return false
        }
      }
      localStorage.setItem(message, message);
      this.todoLists.push(message);
    },
    clearAll() {
      this.todoLists = [];
    },
    showModalExist() {
      this.showModal = false;
    },
    showModalClose() {
      this.showModalMod = false;
    },
    todoModPop(todoList, index) {
        this.showModalMod = true;
        this.message = todoList;
        this.number = index;
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
body {
    text-align:center;
    background-color: #f6f6f8;
}
input {
  border-style: groove;
  width: 200px;
}
button{
  border-style: groove;
}
.shadow {
  box-shadow: 5px 10px 10px rgba(0,0,0,0.03)
}
</style>
