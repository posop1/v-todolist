<template>
  <div class="Todoitem">
    <div class="descrip">
      <span class="title" v-if="!todo.completed">
        {{ todo.title }}
      </span>
      <span class="title" v-if="todo.completed">
        <s>{{ todo.title }}</s>
      </span>
    </div>
    <my-button v-if="!todo.completed"
      @click="$emit('remove', todo)"
    >
      Delete
    </my-button>
    <div class="btn" v-else>
      <my-button 
        @click="$emit('remove', todo)"
        class="remove"
      >
        Return Note
      </my-button>
      <my-button 
        @click="$emit('delete', todo)"
      >
        Delete
      </my-button>
    </div>
    
  </div>
</template>

<script>
import MyButton from './UI/MyButton.vue'
export default {
  components: { MyButton },
    props: {
        todo: {
            type: Object
        }
    }
}
</script>

<style lang="scss" scoped>
.Todoitem{
  background: rgba(0, 0, 0, 0.877);
  color: whitesmoke;
  margin-bottom: 30px;
  padding: 25px;
  border-radius: 10px;
  box-shadow: 0 2px 5px rgba(0,0,0,0.2), 0 4px 6px rgba(0,0,0,0.2);

  display: flex;
  justify-content: space-between;
  align-items: center;
  &:last-child{
    margin-bottom: 0;
  }
}
.descrip{
  display: flex;
  flex-direction: column;
}
.title{
  font-size: 20px;
}
.time{
  font-size: 14px;
  opacity: 0.6;
  margin-right: 8px;
}
.remove{
  margin-right: 30px;
}
</style>