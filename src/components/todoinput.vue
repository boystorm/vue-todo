<template>
    <div class="shadow input-box">
        <input type="text" v-model="message" v-on:keyup.enter="todoList">
        <span class="add-container" v-on:click="todoList">
            <i class="add-btn fas fa-plus"></i>
        </span>

        <modal v-if="showModal" >
            <h3 slot="header">경고</h3>
            <span slot="footer" @click="showModal = false">
                할일을 입력하세요
                <i class="close-modal-btn fas fa-times"></i>
            </span>
        </modal>
    </div>    
</template>

<script>
import Modal from './common/Modal.vue';
export default {
    components: { 
      Modal
    }, 
    data() {
        return{
            message: '',
            showModal: false
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
                this.showModal = !this.showModal
            }

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