<template>
  <div class="flex flex-1 flex-col">
    <ImageThumbnail :thumbnail="product.imgURL" />
    <div class="mt-8 flex justify-start gap-2.5">
      <img :src="star" alt="rating" width="24" height="24" />
      <p class="font-montserrat text-xl leading-normal text-slate-gray">
        ({{ product.rating }})
      </p>
    </div>
    <h3 class="text-2xl leading-normal font-palanquin font-semibold mt-2">
      {{ product.name }}
    </h3>
    <p
      class="text-2xl leading-normal font-montserrat text-coral-red font-semibold mt-2"
    >
      {{ product.price }}
    </p>
  </div>
</template>

<script setup>
import { ImageThumbnail } from "@/components";
import { star } from "@/assets/icons";
const props = defineProps({
  product: {
    type: Object,
    required: true,
  },
});
</script>
