<script lang="ts">
import { defineComponent } from "vue";
import type { PropType } from "vue";

import Card from "../card/Card.vue";

import type { IUser } from "@/assets/interfaces/interfaces";

export default defineComponent({
  props: {
    users: {
      type: Array as PropType<IUser[]>,
      required: true,
    },
  },
  components: {
    Card,
  },
  setup(props) {
    return { ...props };
  },
});
</script>

<template>
  <div class="user-cards">
    <Card v-for="user in users" :key="user.id" :user="user" />
  </div>
</template>

<style scoped>
.user-cards {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
