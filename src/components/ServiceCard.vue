<template>
  <div
    class="flex flex-col flex-1 sm:w[350px] sm:min-w-[350px] w-full rounded-[20px] shadow-3xl px-10 py-16"
  >
    <div
      class="size-11 flex justify-center items-center bg-coral-red rounded-full"
    >
      <img :src="service.imgURL" :alt="service.label" width="24" height="24" />
    </div>
    <h3 class="mt-5 font-palanquin text-3xl leading-normal font-bold">
      {{ service.label }}
    </h3>
    <p class="mt-3 font-montserrat info-text">
      {{ service.subtext }}
    </p>
  </div>
</template>

<script setup>
const props = defineProps({
  service: {
    type: Object,
    required: true,
  },
});
</script>
