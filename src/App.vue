<template>
  <div class="container-fluid">
    <div class="container">
      <Navbar />
      <Transition name="router">
        <RouterView />
      </Transition>
    </div>
  </div>
</template>

<script setup>
import Navbar from "./components/Navbar.vue";
</script>

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
  position: relative;
}
.router-enter-from {
  opacity: 0;
  transform: translateX(-50px);
}
.router-enter-to {
  opacity: 1;
  transform: translateX(0);
}
.router-enter-active {
  transition: all 1s ease;
}
</style>
