<template>
  <!-- relative overflow-hidden shadow-2xl transition-all before:absolute before:h-0 before:w-0 before:rounded-full before:bg-white before:text-coral-red before:duration-500 before:ease-out hover:before:h-56 hover:before:w-56 -->
  <button
    class="cursor-pointer flex justify-center items-center gap-2 px-7 py-4 border border-coral-red font-montserrat text-lg rounded-full bg-coral-red text-white"
  >
    {{ label }}
    <img
      :src="iconURL"
      alt="arrow right icon"
      class="ml-2 rounded-full w-5 h-5"
    />
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
    required: true,
  },
});
</script>
