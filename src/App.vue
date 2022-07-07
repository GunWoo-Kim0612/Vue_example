<template>
  <div id="app">
    <ToDoHeader></ToDoHeader>
    <ToDoInput></ToDoInput>
    <ToDoList ></ToDoList>
    <ToDoFooter></ToDoFooter>

  </div>
</template>
<script>

import TodoHeader from './components/TodoHeader.vue'
import TodoFooter from './components/TodoFooter.vue'
import TodoList from './components/TodoList.vue'
import TodoInput from './components/TodoInput.vue'

export default {
  name: 'app',
  data() {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  // 지역컴퍼넌트 형태로 .vue 컴퍼넌트들 등록
  components: {
    'ToDoHeader': TodoHeader,
    'ToDoFooter': TodoFooter,
    'ToDoInput': TodoInput,
    'ToDoList': TodoList

  }
}
</script>

<style>
body {
  text-align: center;
  background-color: #f6f6f8;
}

input {
  border-style: groove;
  width: 200px;
}

button {
  border-style: groove;
}
.shadow{
  box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03);
}
</style>
