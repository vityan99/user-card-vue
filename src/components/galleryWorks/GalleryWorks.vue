<script lang="ts">
import { defineComponent } from "vue";
import type { PropType } from "vue";

import Work from "../work/Work.vue";
import WorkSkeleton from "../workSkeleton/WorkSkeleton.vue";

import type { IPhotos } from "@/assets/interfaces/interfaces";

export default defineComponent({
  props: {
    works: {
      type: Array as PropType<IPhotos[]>,
      required: true,
    },
  },
  components: {
    Work,
    WorkSkeleton,
  },
  setup(props) {
    return {
      ...props,
    };
  },
});
</script>

<template>
  <div class="gallery-works">
    <div class="gallery-works__content" v-if="works.length > 0">
      <Work v-for="(work, i) in works" :key="i" :work="work.url" />
    </div>
    <div class="gallery-works__content" v-else>
      <WorkSkeleton v-for="i in 6" :key="i" />
    </div>
  </div>
</template>

<style scoped>
.gallery-works {
  padding: 5px 5px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  width: 100%;
}

.gallery-works__content {
  display: flex;
  width: 100%;
  flex-wrap: wrap;
  justify-content: space-between;
}
</style>
