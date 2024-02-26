<template>
  <div class="flex flex-col justify-center items-center">
    <img
      :src="review.imgURL"
      alt="customer profile image"
      class="rounded-full object-contain size-[120px]"
    />
    <p class="info-text mt-6 max-w-sm text-center">{{ review.feedback }}</p>
    <div class="mt-3 flex justify-center items-center gap-2.5">
      <img :src="star" alt="star" class="object-contain m-0" />
      <p class="font-montserrat text-xl text-slate-gray">
        ({{ review.rating }})
      </p>
    </div>
    <h3 class="mt-1 font-palanquin text-3xl text-center font-bold">
      {{ review.customerName }}
    </h3>
  </div>
</template>

<script setup>
import { star } from "@/assets/icons";

const props = defineProps({
  review: {
    type: Object,
    required: true,
  },
});
</script>
