<script setup>
import { ref, computed } from "vue";

const roomId = ref("a");
const num = ref(1);

const config = useRuntimeConfig();
console.log(config.public.baseURL);

const desktopImageSrc = computed(
  () => `${config.public.baseURL}/images/room-${roomId.value}-${num.value}.png`
);
const mobileImageSrc = computed(
  () =>
    `${config.public.baseURL}/images/room-${roomId.value}-sm-${num.value}.png`
);
</script>

<template>
  <picture>
    <source :srcset="desktopImageSrc" media="(min-width: 768px)" />
    <img
      class="w-100 object-fit-cover"
      :src="mobileImageSrc"
      loading="lazy"
      :alt="`room-${roomId}-${num}`"
    />
  </picture>
</template>
