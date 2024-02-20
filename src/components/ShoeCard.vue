<template>
  <div>
    <div
      class="border-2 rounded-xl cursor-pointer max-sm:flex-2"
      :class="{ 'border-coral-red': bigShoeImage === imgURL.bigShoe }"
      @click="handleClick(imgURL.bigShoe)"
    >
      <div
        class="flex justify-center items-center bg-card bg-center bg-cover sm:w-40 sm:h-40 max-sm:p-4"
      >
        <img
          :src="imgURL.thumbnail"
          alt="shoe collection"
          width="127"
          height="103"
        />
      </div>
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
});

const emit = defineEmits(["changeBigShoeImage"]);

const handleClick = (shoeName) => {
  emit("changeBigShoeImage", shoeName);
};
</script>
