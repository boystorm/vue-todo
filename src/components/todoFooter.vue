<template>
    <div class="clear-all-container">
        <span class="clear-all-btn shadow" type="button" v-on:click="clearAll">전체 삭제</span>
    </div>
</template>

<script>
export default{
    methods: {
        clearAll: function(){
            this.$emit('clearAll');
            localStorage.clear();
        }
    }
}
</script>

<style scoped>
.clear-all-container {
    width: 8.5rem;
    height: 50px;
    line-height: 50px;
    background-color: white;
    border-radius: 5px;
    margin: 0 auto;
}
.clear-all-btn{
    color: #e20303;   
}
</style>