<template>
  <div>
    <div
      class="border-2 rounded-xl cursor-pointer max-sm:flex-2"
      :class="{ 'border-coral-red': isHero && bigShoeImage === imgURL.bigShoe }"
      @click="handleClick(imgURL.bigShoe)"
    >
      <ImageThumbnail
        :thumbnail="imgURL.thumbnail"
        :imgURL="imgURL"
        :bigShoeImage="bigShoeImage"
        :isHero="isHero"
      />
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  bigShoeImage: {
    type: String,
    required: true,
  },

  imgURL: {
    type: Object,
    required: true,
  },
  isHero: {
    type: Boolean,
    default: false,
    required: false,
  },
});

import ImageThumbnail from "./ImageThumbnail.vue";

const emit = defineEmits(["changeBigShoeImage"]);

const handleClick = (shoeName) => {
  emit("changeBigShoeImage", shoeName);
};
</script>
