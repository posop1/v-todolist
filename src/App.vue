<template>
  <div class="app">
    <v-header>
      <my-button @click="openDialog">Create Notes</my-button>
      <my-dialog v-model:open="dialogVisible">
        <todo-form  @create='createTodo' />  
      </my-dialog>
    </v-header>
    <todo-list 
      :todos='todos'
      @remove='removeTodo'
      @delete='deleteTodo'
      v-if="!isTodosLoading"
    />
    <div class="loading" v-else-if="isTodosLoading">
      Идёт закрузка
    </div>
  </div>
</template>

<script>
import vHeader from '@/components/vHeader';
import TodoList from '@/components/TodoList'
import TodoForm from '@/components/TodoForm'

import axios from 'axios'

export default {
  components: { vHeader, TodoList, TodoForm },
  
  data() {
    return {
      todos: [],
      dialogVisible: false,
      isTodosLoading: false
    }
  },

  methods: {
    createTodo(todo) {
      this.todos.unshift(todo)
      this.dialogVisible = false
    },
    removeTodo(todo) {
      todo.completed = !todo.completed
    },
    deleteTodo(todo) {
      this.todos = this.todos.filter(t => t.id !== todo.id)
    },
    openDialog() {
      this.dialogVisible = true
    },
    async fetchTodos(){
      try {
        this.isTodosLoading = true
        setTimeout( async() =>{
          const res = await axios.get('http://jsonplaceholder.typicode.com/todos?_limit=20')
          this.todos = res.data
          this.todos = this.todos.reverse()
        }, 1000)
      }catch(e){
        alert('Ошибка')
      }finally {
        this.isTodosLoading = false
      }
    },
  },

  mounted() {
    this.fetchTodos()
  },
};
</script>

<style lang="scss">
html,
body,
div,
span,
applet,
object,
iframe,
h1,
h2,
h3,
h4,
h5,
h6,
p,
blockquote,
pre,
a,
abbr,
acronym,
address,
big,
cite,
code,
del,
dfn,
em,
img,
ins,
kbd,
q,
s,
samp,
small,
strike,
sub,
sup,
tt,
var,
b,
u,
i,
center,
dl,
dt,
dd,
ol,
ul,
li,
fieldset,
form,
label,
legend,
table,
caption,
tbody,
tfoot,
thead,
tr,
th,
td,
article,
aside,
canvas,
details,
embed,
figure,
figcaption,
footer,
header,
hgroup,
menu,
nav,
output,
ruby,
section,
summary,
time,
mark,
audio,
video {
  margin: 0;
  padding: 0;
  border: 0;
  font-size: 100%;
  font-family: "Roboto", sans-serif;
  vertical-align: baseline;
}
/* HTML5 display-role reset for older browsers */
article,
aside,
details,
figcaption,
figure,
footer,
header,
hgroup,
menu,
nav,
section {
  display: block;
}
body {
  line-height: 1;
  box-sizing: border-box;
}
ol,
ul {
  list-style: none;
}
blockquote,
q {
  quotes: none;
}
blockquote:before,
blockquote:after,
q:before,
q:after {
  content: "";
  content: none;
}
table {
  border-collapse: collapse;
  border-spacing: 0;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
}
</style>