<template lang="">
  <div>
    <ul>
      <li
        v-for="(todoItem, index) in propsdata"
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
        <button class="removeBtn" v-on:click="removeTodo(todoItem, index)">
          delete
        </button>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  props: ["propsdata"],
  methods: {
    removeTodo: function (todoItem, index) {
      //console.log(todoItem, index);
      this.$emit("removeItem", todoItem, index);
    },
    toggleComplete: function (todoItem, index) {
      this.$emit("toggleItem", todoItem, index);
    },
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
</style>
