<template>
  <button class="btn">
    <slot></slot>
  </button>
</template>

<script>
export default {
    name: 'my-button'
}
</script>

<style lang="scss" scoped>
.btn{
    padding: 8px 15px;
    border: none;
    outline: none;
    font-size: 14px;
    font-family: "Roboto", sans-serif;
    background: whitesmoke;
    font-weight: bold;
    cursor: pointer;
    border-radius: 5px;
    transition: 0.2s ease-in-out;
    &:hover{
        background: rgba(245, 245, 245, 0.123);
        color: whitesmoke;
    }
}
</style>