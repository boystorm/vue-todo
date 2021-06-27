<template>
    <ul>
        <li v-for="(todoList, index) in propsdata" v-bind:key="todoList">
            <i class="check-btn fas fa-check"></i>
            {{ todoList }}
            
            <div class="crud-btn">
                <span class="mod-btn" type="button">
                    <i class="fas fa-pencil-alt"></i>
                </span>
                <span class="remove-btn" type="button" v-on:click="todoItem(todoList, index)">
                    <i class="far fa-trash-alt"></i>
                </span>
            </div>
        </li>
        <modal v-if="showModal" >
            <h3 slot="header">경고</h3>
            <span slot="footer" v-on:click="showModal2">
                할일이 존재합니다.
                <i class="close-modal-btn fas fa-times" ></i>
            </span>
        </modal>
    </ul>
</template>

<script>
// ul li에 data 스토리지에 있는 데이터 넣어주기
import Modal from './common/Modal.vue';

export default { 
    props: ['propsdata','showModal'],
    components: {
        Modal
    },
    methods: {
        todoItem: function(todoList, index){
            localStorage.removeItem(todoList);
            this.propsdata.splice(index, 1);
        },
        showModal2: function(){
            this.$emit('showModal2')
        }
    }
}
</script>


<style scoped>
ul {
    list-style-type: none;
    padding-left: 0px;
    margin-top: 0;
    text-align: left;
}
li {
    display: flex;
    min-height: 50px;
    height: 50px;
    margin: 0.5rem 0;
    padding: 0 0.9rem;
    background: white;
    border-radius: 5px; 
    line-height: 50px;
}
.crud-btn{
    margin-left: auto;
}
.check-btn{
    line-height: 50px;
    color: #62acde;
    margin-right: 15px;
}
.remove-btn{
    margin-left: 15px;
    color: #de4343;
    line-height: 50px;
}
</style>
