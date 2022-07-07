<template>
  <div>
    <button class="clearAllContainer">
      <span class="clearAllBtn" v-on:click="clearTodo">ClearAll</span>
    </button>

  </div>
</template>

<script>

// 이벤트버스 객체 생성
// let EventBus = new Vue()



// import Vue from 'vue';
export default {


  methods :{
    clearTodo(){
      // 로컬스토리지 모두삭제
      localStorage.clear();
      // EventBus.$emit('message')
      // 삭제이후 리스트목록도 사라지도록...
    }
  }
}
</script>

<style scoped>
.clearAllContainer{
  width: 8.5rem;
  height: 50px;
  line-height: 50px;
  background-color: white ;
  border-radius: 5px;
  margin: 0 auto;
}
.clearAllBtn{
  color: #e20303;
  display: block;
}
</style>
