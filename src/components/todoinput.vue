<template>
    <div>
        <input v-model="message" >
        <button type="button" v-on:click="todoList">추가</button>
    </div>    
</template>

<script>
export default { 
    data() {
        return{
            message: ''
        }
    },
    // 스토리지에 key value 담기
    methods: {
        todoList: function() {
            localStorage.setItem(this.message, this.message);
            this.clearVal();
        },
        clearVal: function() {
            this.message = ''
        }
    }
}
</script>

<style scoped>
input{
    border: 1px solid #999;
    width: 95%;
    height: 35px;
    border-radius: 5px;
}
button {
    height: 35px;
    background: #ddd;
    border: none;
}
</style>