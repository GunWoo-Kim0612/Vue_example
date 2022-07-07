<template>
  <header>
    <div class="inputBox shadow">
      <!-- v-on:keyup.enter : 엔터키에 대해 keyup시 이벤트 발생 -->
      <input type="text" v-model="newTodoItem" placeholder="Type What You Have To Do" v-on:keyup.enter="addTodo">
      <!-- <button v-on:click="addTodo">추가</button> -->
      <span class="addContainer" v-on:click="addTodo">
  <!-- fa fa-plus 는   <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css"> 여기서 확인..버튼  -->
        <i class="addBtn fa fa-plus" aria-hidden="true"></i>
      </span>


    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      // v-model로 폼값 동기화, 문자열로 저장
      newTodoItem: '',
    }
  },
  methods: {
    // 추가버튼 이벤트로 동기화된 문자열 받아오고
    addTodo() {

      //스토리지에 저장

      if (this.newTodoItem != '') {
        let value = this.newTodoItem && this.newTodoItem.trim();  //trim()좌우 공백제거
        //  localStorage.setItem(this.newTodoItem, this.newTodoItem)
        localStorage.setItem(value, JSON.stringify(value))
        this.clearInput();
      }
    },
    //  값 추가 이후(버튼이벤트) input(text) 빈값으로 초기화
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
/* span태그 block형태 */
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
