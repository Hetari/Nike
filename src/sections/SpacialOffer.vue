<template>
  <section
    class="flex justify-start items-center max-xl:flex-col-reverse gap-10 max-container"
  >
    <div class="flex-1">
      <img :src="offer" alt="spacial offer" class="object-contain w-full" />
    </div>

    <div class="flex flex-1 flex-col">
      <h2
        class="capitalize mt-10 font-palanquin text-4xl font-bold lg:max-w-lg"
      >
        <span class="text-coral-red">spacial</span> offer
      </h2>

      <p class="mt-4 lg:max-w-lg info-text">
        Embark on a shopping journey that redefines your experience with
        unbeatable deals. From premier selections to incredible savings, we
        offer unparalleled value that sets us apart.
      </p>
      <p class="mt-6 lg:max-w-lg info-text">
        Navigate a realm of possibilities designed to fulfill your unique
        desires, surpassing the loftiest expectations. Your journey with us is
        nothing short of exceptional.
      </p>
      <div class="mt-11 flex gap-4">
        <btn label="Shop now" :iconURL="arrowRight" />
        <btn label="Learn more" :outline="true" />
      </div>
    </div>
  </section>
</template>

<script setup>
import { arrowRight } from "@/assets/icons";
import { offer } from "@/assets/images";
import { btn } from "@/components";
</script>
