<script lang="ts">
import { defineComponent } from "vue";
import type { PropType } from "vue";

export default defineComponent({
  props: {
    title: String as PropType<string>,
    use: String as PropType<string>,
    clickHandler: Function as PropType<() => void>,
  },
  setup(props) {
    return { ...props };
  },
});
</script>

<template>
  <button :class="['btn', `btn--${use}`]" @click="clickHandler">{{ title }}</button>
</template>

<style scoped>
.btn {
  margin: 0;
  padding: 0;
  border: none;
  background-color: transparent;
  border: 1px solid #cecece;
  border-radius: 7px;
  padding: 7px 10px;
  cursor: pointer;
}

.btn:hover {
  opacity: 0.9;
}

.btn--primary {
  background-color: rgb(47, 47, 47);
  color: #fff;
  border: none;
}

.btn--success {
  background-color: yellowgreen;
  color: #fff;
  border: none;
}

.btn--danger {
  background-color: tomato;
  color: #fff;
  border: none;
}

.btn--pay {
  background-color: rgb(255, 98, 0);
  color: #000;
  border: none;
}

.btn--text {
  background-color: transparent;
  color: #000;
  border: none;
}

.btn--link {
  background-color: transparent;
  color: #000;
  border: none;
  text-decoration: underline;
  text-underline-offset: 3px;
}
</style>
