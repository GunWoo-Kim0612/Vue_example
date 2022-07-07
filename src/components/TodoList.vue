
<template>
  <section>
    <ul>
      <!-- props로 받아온 데이터를 todoItems로 대체 -->
      <li v-for="(item, index) in myProps" :key="index" class="shadow">
        <i class="checkBtn fa fa-check" aria-hidden="true">
          {{index}}{{ item }}
        </i>
        <span class="removeBtn" type="button" v-on:click="removeTodo">
          <i class="fa fa-trash-o" aria-hidden="true"></i>
        </span>
      </li>
    </ul>
  </section>
</template>

<script>

export default {
  props : ['myProps'],

  methods : {
    removeTodo(item,index){
      console.log('item 메소드 안 : ', item);
      console.log('index 메소드 안: ', index);

      this.$emit('removeTodo',item, index)
    }
  }
}
</script>

<style scoped>
ul {
  list-style-type: none;
  padding-left: 0px;
  margin-top: 0;
  text-align: left;
}

li {
  display: flex;
  min-height: 50px;
  line-height: 50px;
  margin: 0.5rem 0;
  padding: 0 0.9rem;
  background: white;
  border-radius: 5px;
}

.checkBtn {
  line-height: 45px;
  color: #62acde;
  margin-right: 5px;
}

.removeBtn {
  margin-left: auto;
  color: #de4343;
}
</style>
