<template>
    <ul>
        <li v-for="(todoList, index) in propsdata" v-bind:key="todoList">
            {{ todoList }}
            <button v-on:click="todoItem(todoList, index)">삭제</button>
        </li>
    </ul>
</template>

<script>
// ul li에 data 스토리지에 있는 데이터 넣어주기

export default { 
    props: ['propsdata'],
    methods: {
        todoItem: function(todoList, index){
            localStorage.removeItem(todoList);
            this.propsdata.splice(index, 1);
        }
    }
}
</script>


<style scoped>

</style>
