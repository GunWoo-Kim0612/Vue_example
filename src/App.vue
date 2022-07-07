<template>
  <div id="app">
    <ToDoHeader></ToDoHeader>
    <ToDoInput v-on:addTodo="addTodo"></ToDoInput>
    <!-- 뷰데이터를 받아 사용한 props v-bind:myProps="todoItems" -->
    <ToDoList v-bind:myProps="todoItems" v-on:removeTodo="removeTodo"></ToDoList>
    <ToDoFooter v-on:removeAll="removeAll"></ToDoFooter>

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
      msg: 'Welcome to Your Vue.js App',
      todoItems: [],
    }
  },


  // 라이프사이클함수..시작과동시에 스토리지 데이터 불러와 배열에 렌더링..App.vue로 이동
  created() {
    if (localStorage.length > 0) {
      for (let i = 0; i < localStorage.length; i++) {
        if (localStorage.key(i) == "loglevel:webpack-dev-server") {
        }
        if (localStorage.key(i) != "loglevel:webpack-dev-server") {
          this.todoItems.push(localStorage.key(i));
        }
      }
    }
  },




methods:{

  // TodoInput(자식) 쪽에서 뷰데이터를 부모로 전달(event 매개변수를 통해...)
  addTodo(item) {
    localStorage.setItem(item, item);
    this.todoItems.push(item);
  },
  removeTodo(item, index) {
    console.log('index: ', index);
    localStorage.removeItem( index, item);
    this.todoItems.splice(index, 1);
  },
  removeAll() {
    localStorage.clear();
    // 리스트배열 빈배열로 초기화
    this.todoItems = [];
  },
},


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

.shadow {
  box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03);
}
</style>
