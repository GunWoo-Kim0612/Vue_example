<template>
  <header>
    <div class="inputBox shadow">
      <input type="text" v-model="newTodoItem" placeholder="Type What You Have To Do" v-on:keyup.enter="addTodo">
      <span class="addContainer" v-on:click="addTodo">
        <i class="addBtn fa fa-plus" aria-hidden="true"></i>
      </span>


    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      newTodoItem: '',
    }
  },
  methods: {
    addTodo() {

      if (this.newTodoItem != '') {
        let value = this.newTodoItem && this.newTodoItem.trim();
        let index = this.newTodoItem.indexOf();
        // 스토리지 기능은 App으로 넘겨줬고 event를 발생시켜 App에서 동작하게끔
        this.$emit('addTodo', value, index)  // 매개변수 ('이벤트명', 값)
        // localStorage.setItem(value, JSON.stringify(value))
        this.clearInput();
      }
    },
    clearInput() {
      this.newTodoItem = '';
    }
  }

}

</script>

<style scoped>
input:focus {
  outline: none;
}

.inputBox {
  background-color: white;
  ;
  height: 50px;
  line-height: 50px;
  border-radius: 5px;
}
.inputBox input{
  border-style: none;
  font-size: 0.9rem;
}
.addContainer{
  float: right;
  background: linear-gradient(to right, #ccc,#ccc);
  /* display: inline-block; */
  width: 3rem;
  border-radius: 0 5px 5px 0;
}
/* .addBtn{

} */
</style>
