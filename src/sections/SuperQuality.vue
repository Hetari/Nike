<template>
  <section
    id="about-us"
    class="flex justify-between items-center max-lg:flex-col gap-10 w-full max-container"
  >
    <div class="flex flex-1 flex-col">
      <h2 class="heading-title">
        we provide you <span class="text-coral-red">super</span>
        <span class="text-coral-red inline-block">quality</span> shoes
      </h2>

      <p class="mt-4 lg:max-w-lg info-text">
        Ensuring premium comfort and style, our meticulously crafted footwear is
        designed to elevate your experience, providing you with unmatched
        quality, innovation, and a touch of elegance.
      </p>
      <p class="mt-6 lg:max-w-lg info-text">
        Our dedication to detail and excellence ensures your satisfaction
      </p>
      <div class="mt-11">
        <btn label="View details" />
      </div>
    </div>
    <div class="flex flex-1 justify-center items-center">
      <img
        :src="shoe8"
        alt="nice shoes"
        width="570"
        height="522"
        class="object-contain"
      />
    </div>
  </section>
</template>

<script setup>
import { shoe8 } from "@/assets/images";
import { btn } from "@/components";
</script>
