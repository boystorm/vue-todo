<template>
    <div class="todo-title">
        <h3 class="static" v-bind:class="{active: isActive}">{{ message }}</h3>
    </div>
</template>

<script>
export default { 
  name: 'todoheader',
  data () {
    return{
        message: "Hello Todo It!",
        isActive: true
    }
  }
}
</script>

<style scoped>
.todo-title {
    display: flex;
    justify-content: center;
}
.static{
    color: cornflowerblue;
    font-size: 34px;
}
</style>