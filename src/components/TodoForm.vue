<template>
  <form @submit.prevent>
    <my-input v-model="todo.title" placeholder="ToDo title..." />
    <my-button @click="createTodo"> ADD </my-button>
  </form>
</template>

<script>
import MyButton from "./UI/MyButton";
import MyInput from "./UI/MyInput";
export default {
  components: { MyInput, MyButton },

  data() {
    return {
      todo: {
        title: "",
      },
    };
  },
  
  methods: {
    createTodo() {
      this.todo.id = Date.now();
      this.comleted = false
      this.$emit("create", this.todo);
      this.todo = {
        title: "",
      };
    },
  },
};
</script>

<style lang="scss" scoped>
form {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
}
</style>