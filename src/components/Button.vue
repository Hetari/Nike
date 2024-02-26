<template>
  <button
    class="cursor-pointer font-montserrat text-lg relative px-6 py-3 font-bold text-white group"
    :class="{
      'w-full': fullWidth,
    }"
  >
    <span
      class="absolute inset-0 size-full transition duration-300 ease-out transform -translate-x-2 -translate-y-2 group-hover:translate-x-0 group-hover:translate-y-0 rounded-full"
      :class="{
        'bg-black ': outline,
        ' bg-coral-red': !outline,
      }"
    ></span>
    <span
      class="absolute inset-0 w-full h-full border-[3px] rounded-full"
      :class="{
        'border-gray-400 ': outline,
        'border-black ': !outline,
      }"
    ></span>
    <span class="relative flex justify-center items-center gap-2">
      {{ label }}
      <img
        v-if="iconURL"
        :src="iconURL"
        alt="arrow right icon"
        class="ml-2 rounded-full w-5 h-5"
      />
    </span>
  </button>
</template>

<script setup>
const props = defineProps({
  label: {
    type: String,
    required: true,
  },
  iconURL: {
    type: String,
    required: false,
  },
  outline: {
    type: Boolean,
    default: false,
    required: false,
  },
  fullWidth: {
    type: Boolean,
    default: false,
    required: false,
  },
});
</script>
