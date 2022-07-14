<template>
  <div class="header">
    <div class="container inner">
        <h1>TodoList</h1>
        <slot></slot>
    </div>
  </div>
</template>

<script>

export default {

  props: {
    todos: {
      type: Array,
    }
  },
}
</script>

<style lang="scss" scoped>
.header{
  width: 100%;
  background: rgba(0, 0, 0, 0.877);
  padding: 15px 0;
}
.inner{
  display: flex;
  justify-content: space-between;
  align-items: center;
}
h1{
  font-size: 32px;
  color: white;
}
</style>