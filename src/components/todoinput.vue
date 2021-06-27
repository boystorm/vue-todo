<template>
    <div class="shadow input-box">
        <input type="text" v-model="message" v-on:keyup.enter="todoList">
        <span class="add-container" v-on:click="todoList">
            <i class="add-btn fas fa-plus"></i>
        </span>
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
            if(value != ''){
                this.$emit('todoList', value);
            }else{
                alert("할일을 입력해 주세요")
            }

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
    width: 95%;
    height: 35px;
    border-radius: 5px;
    border: none;
}
input:focus {
    outline: none;
}
.input-box{
    background: white;
    height: 50px;
    line-height: 50px;
    border-radius: 5px;
}
.add-container{
    float: right;
    display:block;
    width: 3rem;
    background: #333;
}
.add-btn{
    color: white;
}
</style>