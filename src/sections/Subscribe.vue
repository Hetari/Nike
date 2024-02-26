<template>
  <section
    id="contact-us"
    class="max-container flex justify-between items-center max-lg:flex-col gap-8 max-sm:text-center"
  >
    <h3 class="heading-title">
      Sign Up for
      <span class="text-coral-red"> Updates </span> & Newsletter
    </h3>
    <div
      class="lg:max-w-[40%] w-full flex items-center max-sm:flex-col gap-5 p-2.5 sm:border sm:border-slate-gray rounded-full"
    >
      <input type="text" placeholder="subscribe@nike.com" class="input" />
      <div class="flex max-sm:justify-end items-center max-sm:w-full">
        <btn label="Sign Up" :fullWidth="true" />
      </div>
    </div>
  </section>
</template>

<script setup>
import { btn } from "@/components";
</script>
