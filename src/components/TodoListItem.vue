<template>
  <li>
    <span class="item" :class="todoItemClass" @click="toggleItem">
      {{ todoItem.title }}
    </span>
    <button v-on:click="removeItem">삭제</button>
  </li>
</template>
<script lang="ts">
import { Todo } from "@/App.vue";
import Vue, { PropType } from "vue";
export default Vue.extend({
  props: {
    todoItem: Object as PropType<Todo>,
    index: Number,
  },
  computed: {
    todoItemClass(): string | null {
      return this.todoItem.done ? "complate" : null;
    },
  },
  methods: {
    toggleItem() {
      this.$emit("toggle", this.todoItem, this.index);
    },
    removeItem() {
      console.log("removeTodo");
      this.$emit("remove", this.index);
    },
  },
});
</script>
<style scoped>
.item {
  cursor: pointer;
}
.complate {
  text-decoration: line-through;
}
</style>
