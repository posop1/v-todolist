<template>
  <div class="TodoList" v-if="todos.length > 0">
    <div class="container">
        <todo-item 
          :key="todo.id" 
          v-for="todo in todos" 
          :todo='todo'
          @remove="$emit('remove', todo)"
        />
    </div>
  </div>
  <div class="TodoEmpty" v-else>
    <div class="container inner">
      <h2>Todo is empty</h2>
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
.TodoEmpty {
  margin-top: 100px;
}
.inner{
  display: flex;
  justify-content: center;
  h2{
    font-size: 40px;
  }
}
</style>