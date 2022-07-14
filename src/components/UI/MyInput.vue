<template>
  <input 
    type="text"
    :value="modelValue"
    @input="updateInput"
    class="input"
  />
</template>

<script>
export default {
    name: 'my-input',
    props: {
        modelValue: [String, Number]
    },

    methods: {
        updateInput(event) {
            this.$emit('update:modelValue', event.target.value)
        }
    }
}
</script>

<style lang="scss" scoped>
.input {
  width: 300px;
  outline: none;
  border: none;
  padding: 8px;
  font-size: 14px;
  background: whitesmoke;
  font-family: "Roboto", sans-serif;
  border-radius: 2px;
}
</style>