<!-- 뷰데이터 변경시 재 렌더링 추가할 리스트 항목이 새로고침 없이 나타남 -->

<template>
  <section>
    <ul>
      <!-- 스토리지 값을 key을 통해 반복시 문법형태  -->
      <!-- v-for="(element, index) in Array" : key="i" -->
      <!-- :key='index >>>' v-bind:key="index" -->
      <li v-for="(item, index) in todoItems" :key="item" class="shadow">
        <i class="checkBtn fa fa-check" aria-hidden="true">
          {{index}}{{ item }}
          <!-- key값 {{i}} 로 확인 가능 -->
        </i>
        <span class="removeBtn" type="button" v-on:click="removeTodo(item,index)">
          <i class="fa fa-trash-o" aria-hidden="true"></i>
           <span class="clearAllBtn" v-on:click="EventBus">ClearAll</span>
        </span>
      </li>
    </ul>
  </section>
</template>

<script>

export default {
  data() {
    return {
      // 로컬스토리지에서 가져와 뷰데이터로 반환, 배열형태로...
      todoItems: [],
    }
  },
  created() {
    // 로컬스토리지 크기가 0보다 크면
    if (localStorage.length > 0) {
      for (let i = 0; i < localStorage.length; i++) {
        if(localStorage.key(i) == "loglevel:webpack-dev-server"){
          console.log('localStorage.removeItem(i): ', localStorage.removeItem(i));
        }
        if (localStorage.key(i) != "loglevel:webpack-dev-server") {
          this.todoItems.push(localStorage.key(i));
        }
        // 스토리지에있는(배열형태) index를 매개로 값을 todoItem[] 에 push()
      }
    }
  },
  methods: {
    removeTodo(item,index){
      console.log('index: ', index);
      // removeItem() :
      localStorage.removeItem(item);
      this.todoItems.splice(index,1);
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
  height: 50px;
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
