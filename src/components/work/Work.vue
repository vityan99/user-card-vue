<script lang="ts">
import { defineComponent } from "vue";
import type { PropType } from "vue";

export default defineComponent({
  props: {
    work: String as PropType<string>,
  },
  setup(props) {
    return {
      ...props,
    };
  },
});
</script>

<template>
  <div class="work">
    <img class="work__img" :src="work" alt="work" />
  </div>
</template>

<style scoped>
.work {
  width: calc(100% / 3 - 5px);
  height: 100px;
  margin-bottom: 5px;
}

.work__img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 5px;
}
</style>
