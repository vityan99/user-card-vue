<script setup lang="ts">
import { users } from "./assets/config";
import UserCards from "./components/userCards/UserCards.vue";
</script>

<template>
  <div class="container">
    <UserCards :users="users" />
  </div>
</template>

<style scoped>
.container {
  display: flex;
  height: 100vh;
  align-items: center;
  justify-content: center;
}
</style>
