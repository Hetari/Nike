<template>
  <div
    class="rounded-xl flex justify-start items-center bg-center bg-cover max-sm:p-4"
    :class="{ 'bg-card sm:w-40 sm:h-40 justify-center': isHero }"
  >
    <img
      :src="thumbnail"
      alt="shoe collection"
      :width="isHero ? 127 : 280"
      :height="isHero ? 103 : 280"
      :class="{
        grayscale: isHero,
        'grayscale-0': isHero && bigShoeImage === imgURL.bigShoe,
      }"
    />
  </div>
</template>

<script setup>
const props = defineProps({
  bigShoeImage: {
    type: String,
    default: "",
    required: false,
  },

  imgURL: {
    type: Object,
    required: false,
  },
  isHero: {
    type: Boolean,
    default: false,
    required: false,
  },
  thumbnail: {
    type: String,
    required: true,
  },
});
</script>
