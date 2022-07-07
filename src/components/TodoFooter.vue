<template>
  <div>
    <button class="clearAllContainer" v-on:keyup.enter="removeAll">
      <span class="clearAllBtn" v-on:click="removeAll" >ClearAll</span>
    </button>

  </div>
</template>

<script>

export default {


  methods :{
    removeAll(){
      this.$emit('removeAll')
      // localStorage.clear();
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
