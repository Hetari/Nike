<template>
  <section id="products" class="max-container max-sm:mt-12">
    <div class="flex flex-col justify-start gap-5">
      <h2 class="heading-title">
        our <span class="text-coral-red inline-block">popular</span> products
      </h2>
      <p class="info-text mt-2 lg:max-w-lg text-balance max-sm:mt-0">
        Step into a World of Endless Possibilities: From Everyday Essentials to
        Luxury Finds, Our Product Range Has Something for Everyone!
      </p>
    </div>
    <div class="max-sm:flex max-sm:justify-center max-sm:items-center">
      <div
        class="mt-16 grid lg:grid-cols-4 md:grid-cols-3 sm:grid-cols-2 grid-cols-1 gap-14 sm:gap-4"
      >
        <PopularProductsCard
          class="cursor-pointer"
          v-for="product in products"
          :key="product.id"
          :product="products[product.id]"
        />
      </div>
    </div>
  </section>
</template>

<script setup>
import PopularProductsCard from "@/components/PopularProductsCard.vue";
import { products } from "@/constants";
</script>
