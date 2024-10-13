<script lang="ts">
import { defineComponent, ref } from "vue";
import type { PropType } from "vue";

import type { IUser, IPhotos } from "@/assets/interfaces/interfaces";

import Avatar from "../avatar/Avatar.vue";
import Button from "../button/Button.vue";
import GalleryWorks from "../galleryWorks/GalleryWorks.vue";

export default defineComponent({
  props: {
    user: {
      type: Object as PropType<IUser>,
      required: true,
    },
  },
  components: {
    Avatar,
    Button,
    GalleryWorks,
  },
  setup(props) {
    const { name, img } = props.user;

    const photos = ref<IPhotos[]>([]);
    const online = ref(true);

    const fetchWorks = async () => {
      try {
        const response = await fetch("https://api.slingacademy.com/v1/sample-data/photos?limit=6");
        const data = await response.json();

        photos.value.splice(0, photos.value.length, ...data.photos);
      } catch (error) {
        console.error("Ошибка при загрузке данных:", error);
      }
    };

    return {
      ...props,
      online,
      photos,
      fetchWorks,
      name,
      img,
    };
  },
});
</script>

<template>
  <div class="card">
    <div :class="['card__img-wrapper', { 'user--online': online }]">
      <Avatar :img="img" />
    </div>
    <span class="card__username">{{ name }}</span>
    <Button title="Показать работы" use="success" :clickHandler="fetchWorks" />
    <GalleryWorks :works="photos" />
  </div>
</template>

<style scoped>
.card {
  padding: 25px 20px;
  width: 200px;
  background: radial-gradient(
        ellipse at 65% 90%,
        transparent 0%,
        rgba(121, 155, 213, 0.31) 60%,
        rgba(88, 121, 214, 0.31) 60%,
        rgba(127, 167, 225, 0.29) 100%
      )
      15% 90%/165% 165%,
    linear-gradient(315deg, rgb(110, 78, 203) 0%, rgb(84, 106, 212) 45%, rgb(63, 99, 210) 100%);

  border-radius: 10px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 15px;
}

.card__img-wrapper {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  position: relative;
}

.user--online::after {
  content: "";
  position: absolute;
  top: 5px;
  right: 5px;
  width: 15px;
  height: 15px;
  background-color: rgb(0, 255, 0);
  border-radius: 50%;
  border: 2px solid white;
}

.card__username {
  color: #fff;
}
</style>
