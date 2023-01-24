<template lang="">
  <div class="inputBox shadow">
    <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodoItem" />
    <button v-on:click="addTodo"></button>
    <span class="addContainer" v-on:click="addTodo">
      <i class="fa-solid fa-plus"></i>
    </span>
    <!-- <AlertModal v-if="showModal" @close="showModal = false">
      
      <h3 slot="header">경고</h3>

      아무것도 입력하지 않으셨습니다.
    </AlertModal> -->
  </div>
</template>
<script>
//import AlertModal from "./common/AlertModal.vue";
export default {
  data() {
    return {
      newTodoItem: "",
      showModal: true,
    };
  },
  methods: {
    addTodo() {
      if (this.newTodoItem !== "") {
        this.$emit("addTodoItem", this.newTodoItem);
        this.clearInput();
      }
      //console.log(this.newTodoItem);
      //저장하는 로직을 수행
      // this.newTodoItem = "";
      //var obj = { completed: false, item: this.newTodoItem };
      //localStorage.setItem(this.newTodoItem, JSON.stringify(obj));
    },
    clearInput() {
      this.newTodoItem = "";
    },
  },
  // components: {
  //   AlertModal: AlertModal,
  // },
};
</script>

<style scoped>
input:focus {
  outline: none;
}
.inputBox {
  background: white;
  height: 50px;
  line-height: 50px;
  border-radius: 5px;
}
.inputBox input {
  border-style: none;
  font-size: 0.9rem;
}
.addContainer {
  float: right;
  background: linear-gradient(to right, #6478fb, #8763fb);
  display: block;
  width: 3rem;
  border-radius: 0 5px 5px 0;
}
.addBtn {
  color: white;
  vertical-align: middle;
}
.closeModalBtn {
  color: #42b983;
}
</style>
