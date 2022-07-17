<template>
  <div class="TodoList" v-if="todos.length > 0">
    <div class="container">
      <h2>Notes</h2>
      <div class="item" v-for="todo in todos" :key='todo.id'>
        <todo-item 
          v-if="!todo.completed"
          :todo='todo'
          @remove="$emit('remove', todo)"
          :key="todo.id"
        />
      </div>
      <hr>
      <h2 class="last">Comleted Notes</h2>
      <div class="item" v-for="todo in todos" :key='todo.id'>
        <todo-item 
          v-if="todo.completed"
          :todo='todo'
          :key="todo.id"
          @remove="$emit('remove', todo)"
          @delete="$emit('delete', todo)"
        />
      </div>
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
  },
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
}
.item {
  margin-bottom: 30px;
}
h2{
  font-size: 30px;
  margin-bottom: 35px;
}
.last{
  margin-top: 30px;
}
hr{
  height: 5px;
  background: rgba(0, 0, 0, 0.877);
  border: none;
  border-radius: 10px;
  margin-top: 50px;
}
</style>