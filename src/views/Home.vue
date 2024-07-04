<script setup>
import { ref } from "vue";
import { gsap } from "gsap";
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
function beforeEnter(el) {
  el.style.opacity = 0;
  el.style.transform = "scale(0)";
}
function enter(el) {
  gsap.to(el, {
    opacity: 1,
    duration: 1,
    scale: 1,
    delay: 0.5 * el.dataset.index
  });
}
function afterEnter() {
  console.log("after enter");
}
function beforeLeave() {
  console.log("before leave");
}
function leave() {
  console.log("leave");
}
function afterLeave() {
  console.log("after leave");
}
</script>

<template>
  <main>
    <input
      type="text"
      autofocus
      placeholder="add to task here..."
      v-model="task"
      @keyup.enter="addTasks()"
    />

    <TransitionGroup
      name="item"
      appear
      @before-enter="beforeEnter"
      @enter="enter"
      @after-enter="afterEnter"
      @before-leave="beforeLeave"
      @leave="leave"
      @after-leave="afterLeave"
    >
      <div
        v-for="(task, index) in tasks"
        :key="task"
        class="todo-list"
        @click="deleteTasks(index)"
        :data-index="index"
      >
        {{ task }}
      </div>
    </TransitionGroup>
  </main>
</template>

<style scoped>
main {
  width: 100%;
}
input {
  width: 100%;
  padding: 20px;
  border-radius: 8px;
  margin-bottom: 25px;
  border: 2px solid #949494;
  box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
  box-sizing: border-box;
}
.todo-list {
  border-radius: 8px;
  padding: 20px;
  width: 100%;
  text-align: center;
  margin: 10px 0;
  border: 1px solid #ccc;
  box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
  box-sizing: border-box;
}
/* .item-enter-from {
  opacity: 0;
  transform: scale(0.5);
}
.item-enter-to {
  opacity: 1;
  transform: scale(1);
} */
.item-enter-active {
  transition: all 0.5s ease;
}
.item-move {
  transition: all 0.5s ease;
}
.item-leave-from {
  opacity: 1;
  transform: scale(1);
}
.item-leave-to {
  opacity: 0;
  transform: scale(0);
}
.item-leave-active {
  transition: all 0.5s ease;
  position: absolute;
}
</style>