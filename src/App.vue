<script setup>
</script>

<template>
  <div class="container-fluid">
    <div class="container">
      <input type="text" autofocus />
      <div class="list">
        <div class="todo-list">Task 1</div>
        <div class="todo-list">Task 2</div>
        <div class="todo-list">Task 3</div>
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