<template lang="">
  <div>
    <TransitionGroup name="list" tag="ul">
      <li
        v-for="(todoItem, index) in this.storedTodoItems"
        v-bind:key="todoItem.item"
        class="shadow"
      >
        <button
          class="checkBtn"
          v-bind:class="{ checkBtnCompleted: todoItem.completed }"
          v-on:click="toggleComplete(todoItem, index)"
        >
          click
        </button>
        <span v-bind:class="{ textCompleted: todoItem.completed }">{{
          todoItem.item
        }}</span>
        <button class="removeBtn" v-on:click="removeTodo({ todoItem, index })">
          delete
        </button>
      </li>
    </TransitionGroup>
  </div>
</template>
<script>
import { mapGetters, mapMutations } from "vuex";

export default {
  //props: ["propsdata"],
  methods: {
    ...mapMutations({
      removeTodo: "removeOneItem",
    }),
    // removeTodo(todoItem, index) {
    //   //console.log(todoItem, index);
    //   //this.$emit("removeItem", todoItem, index);
    //   // const obj = {
    //   //   todoItem,
    //   //   index
    //   // }
    //   this.$store.commit("removeOneItem", { todoItem, index });
    // },
    toggleComplete(todoItem, index) {
      //this.$emit("toggleItem", todoItem, index);
      this.$store.commit("toggleOneItem", { todoItem, index });
    },
  },
  computed: {
    // todoItems() {
    //   return this.$store.getters.storedTodoItems;
    // },
    ...mapGetters(["storedTodoItems"]),
    // ...mapGetters({
    //   todoItems: "storedTodoItems",
    // }),
  },
};
</script>
<style scoped>
.textCompleted {
  text-decoration: line-through;
  color: #b3adad;
}
.checkBtnCompleted {
  color: #b3adad;
}
/* 리스트 아이템 트랜지션 효과 */
.list-enter-active,
.list-leave-active {
  transition: all 0.5s;
}
.list-enter, .list-leave-to /* .list-leave-active below version 2.1.8 */ {
  opacity: 0;
  transform: translateY(30px); /* 밑으로 살짝 빠지는 효과 */
}
</style>
