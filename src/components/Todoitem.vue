<template>
  <div class="todoitem">
    <div class="taskshow">
      <input type="checkbox" @change="markcomplete" />
      <span v-bind:class="{ completed: task.completed }">{{ task.title }}</span>
    </div>
    <div class="taskoperationbtn">
      <button @click="showform">update</button>
      <button @click="$emit('deletetask', task.id)">delete</button>
    </div>
    <form @submit="updatetitle" v-if="show">
      <input type="text" v-model="newtitle" />
      <button type="submit">update</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "Todoitem",
  props: ["task"],
  data() {
    return {
      show: false,
      newtitle:""
    };
  },
  methods: {
    markcomplete() {
      this.task.completed = !this.task.completed;
    },
    showform() {
      this.show = !this.show;
    },
    updatetitle(e) {
      e.preventDefault();
      this.task.title=this.newtitle
      this.newtitle=""
      this.show=false
      
    },
  },
};
</script>

<style>
.todoitem {
  margin-top: 20px;
  display: flex;
  justify-content: space-between;
}
.taskshow {
  display: flex;
  margin-left: 50px;
}
.taskshow span {
  margin-left: 20px;
}
.taskoperationbtn {
  margin-right: 50px;
}
.taskoperationbtn button {
  margin-right: 20px;
}
.completed {
  text-decoration: line-through;
}
</style>
