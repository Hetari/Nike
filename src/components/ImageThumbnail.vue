<template>
  <div
    class="rounded-xl flex justify-start items-center bg-center bg-cover"
    :class="{
      'bg-card sm:size-40 justify-center': isHero,
      'transition-all duration-300 hover:scale-105': !isHero,
    }"
  >
    <img
      :src="thumbnail"
      alt="shoe collection"
      :width="isHero ? 127 : 280"
      :height="isHero ? 103 : 280"
      :class="{
        'grayscale ': isHero,
        'grayscale-0 ': isHero && bigShoeImage === imgURL.bigShoe,
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
