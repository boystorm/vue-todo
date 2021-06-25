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
            var value = this.message && this.message.trim();
            // 상위 컴포넌트로 이벤트와 인풋에서 타이핑한 값(value)를 보낸다.
            this.$emit('todoList', value);

            this.clearVal();
        },
        clearVal: function() {
            this.message = ''
        },
        showAlert: function() {
            alert("event")
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