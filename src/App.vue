<template>
  <div class="app">
    <v-header>
      <todo-form  @create='createTodo' />
    </v-header>
    <todo-list 
      :todos='todos'
    />
  </div>
</template>

<script>
import vHeader from './components/vHeader';
import TodoList from '@/components/TodoList'
import TodoForm from '@/components/TodoForm'
export default {
  components: { vHeader, TodoList, TodoForm },
  
  data() {
    return {
      todos: [
        {id: 1, title: 'Todo 1', Datetime: new Date(Date.now()).toLocaleDateString().slice(0,-5), time: new Date(Date.now()).toLocaleTimeString().slice(0,-3)},
        {id: 2, title: 'Todo 2', Datetime: new Date(Date.now()).toLocaleDateString().slice(0,-5), time: new Date(Date.now()).toLocaleTimeString().slice(0,-3)},
        {id: 3, title: 'Todo 3', Datetime: new Date(Date.now()).toLocaleDateString().slice(0,-5), time: new Date(Date.now()).toLocaleTimeString().slice(0,-3)},
        {id: 4, title: 'Todo 4', Datetime: new Date(Date.now()).toLocaleDateString().slice(0,-5), time: new Date(Date.now()).toLocaleTimeString().slice(0,-3)},
      ]
    }
  },

  methods: {
    createTodo(todo) {
      this.todos.push(todo)
    }
  }
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