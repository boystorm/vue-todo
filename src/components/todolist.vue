<template>
    <ul>
        <li v-for="(todoList, index) in todoLists" v-bind:key="todoList">
            {{ todoList }}
            <button v-on:click="todoItem(todoList, index)">삭제</button>
        </li>
    </ul>
</template>

<script>
// ul li에 data 스토리지에 있는 데이터 넣어주기

export default { 
    data (){
        return {
            todoLists: []
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
    methods: {
        todoItem: function(todoList, index){
            localStorage.removeItem(todoList);
            this.todoLists.splice(index, 1);
        }
    }
}
</script>


<style scoped>

</style>
