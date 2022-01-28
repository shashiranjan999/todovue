<template>
  <main>
    <div class="addtodo">
      <input
        class="taskinputbox"
        v-model="title"
        type="text"
        placeholder="Add your Task"
      />
      <button @click="addtodo" class="addtaskbtn">Add</button>
    </div>
    <ShowTodo v-on:deletetask="deleteval" :tasks="tasks" />
  </main>
</template>

<script>
import ShowTodo from "./ShowTodo.vue";
export default {
  name: "AddTodo",
  components: {
    ShowTodo,
  },
  methods: {
    addtodo() {
      this.tasks.push({ id: Date.now(), title: this.title, completed: false });
      this.title = "";
    },
    deleteval(id){  
      
      this.tasks=this.tasks.filter((task)=>{return task.id !== id})
    }
  },
  data() {
    return {
      title: null,
      tasks: [],
    };
  },
};
</script>

<style>
.addtodo {
  text-align: center;
  margin-top: 100px;
}

.taskinputbox {
  padding: 10px;
  outline: none;
}
.addtaskbtn {
  margin-left: 20px;
  width: 100px;
  padding: 10px;
  font-size: 15px;
}
</style>
