<template>
  <div class="Todoitem">
    <div class="descrip">
      <span class="title">{{ todo.title }}</span>
      <span class="time">{{ todo.time }}</span>
    </div>
  </div>
</template>

<script>
export default {
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
  padding-bottom: 18px;
}
.time{
  font-size: 14px;
  opacity: 0.6;
}
</style>