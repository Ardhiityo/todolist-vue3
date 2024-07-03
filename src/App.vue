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
  
        <TransitionGroup name="item">
          
          <div
            v-for="(task, index) in tasks"
            :key="task"
            class="todo-list"
            @click="deleteTasks(index)"
          >
            {{ task }}
          </div>
          
        </TransitionGroup>
   
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
  margin-bottom: 25px;
  border: 2px solid #949494;
  box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
}
.todo-list {
  border-radius: 8px;
  padding: 20px;
  width: 100%;
  text-align: center;
  margin: 10px 0;
  border: 1px solid #ccc;
  box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
}
.item-enter-from {
  opacity: 0;
  transform: scale(0.5);
}
.item-enter-to {
  opacity: 1;
  transform: scale(1);
}
.item-enter-active {
  transition: all 1s ease;
}
</style>