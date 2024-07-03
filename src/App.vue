<script setup>
import { ref } from "vue";
const tasks = ref(["Learn Vue", "Learn Vue Router", "Learn JavaScript"]);
const task = ref("");
function addTasks() {
  if (task.value) {
    tasks.value.unshift(task.value);
    task.value = "";
  }
}
function deleteTasks(index) {
  tasks.value.splice(index, 1);
}
</script>

<template>
  <div class="container-fluid">
    <div class="container">
      <input
        type="text"
        autofocus
        placeholder="add to task here..."
        v-model="task"
        @keyup.enter="addTasks()"
      />
      <div class="list" v-for="(task, index) in tasks" :key="index">
        <div class="todo-list" @click="deleteTasks(index)">{{ task }}</div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.container-fluid {
  width: 100%;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: start;
}
.container {
  width: 60%;
  display: flex;
  align-items: center;
  justify-content: start;
  flex-direction: column;
  margin-top: 30px;
}
input {
  width: 100%;
  padding: 20px;
  border-radius: 8px;
  margin-bottom: 20px;
  border: 2px solid #949494;
  box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
}
.list {
  width: 100%;
  display: flex;
  flex-direction: column;
  gap: 15px;
  margin: 15px 0;
  text-align: center;
}
.todo-list {
  border-radius: 8px;
  padding: 20px;
  border: 1px solid #ccc;
  box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
}
</style>