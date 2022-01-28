<template>
  <div class="showtodo">
    <div v-for="task in tasks" :key="task.id">
      <Todoitem v-on:deletetask="$emit('deletetask', task.id)" :task="task" />
    </div>
  </div>
</template>

<script>
import Todoitem from "./Todoitem.vue";
export default {
  name: "ShowTodo",
  components: {
    Todoitem,
  },
  props: ["tasks"],
};
</script>

<style>
</style>
