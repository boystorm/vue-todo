<template>
    <div>
        <button v-on:click="clearAll">전체 삭제</button>
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
div {
    display: flex;
    margin:0 auto;
}
button {
    background-color: #ddd;
    border: none;
    color: #333
}

</style>