<template>
  <div class="TodoList">
    <div class="container inner">
        <todo-item :key="todo.id" v-for="todo in todos" :todo='todo'/>
    </div>
  </div>
</template>

<script>
import TodoItem from './TodoItem.vue'
export default {
  components: { TodoItem },

  props: {
    todos: {
        type: Array
    }
  }
}
</script>

<style lang="scss" scoped>
.TodoList{
  margin-top: 100px;
}

</style>