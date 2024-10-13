<script lang="ts">
import { defineComponent } from "vue";
import type { PropType } from "vue";

export default defineComponent({
  props: {
    img: String as PropType<string>,
  },

  setup(props) {
    return {
      ...props,
    };
  },
});
</script>

<template><img class="img" :src="img" alt="avatar" /></template>

<style scoped>
.img {
  width: 100%;
  height: 100%;
  border-radius: 100%;
  object-fit: cover;
}
</style>
