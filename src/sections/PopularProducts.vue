<template>
  <section id="products" class="max-container max-sm:mt-12">
    <div class="flex flex-col justify-start gap-5">
      <h2 class="text-4xl font-palanquin font-bold capitalize">
        our <span class="text-coral-red inline-block">popular</span> products
      </h2>
      <p class="font-montserrat text-slate-gray mt-2 lg:max-w-lg">
        Step into a World of Endless Possibilities: From Everyday Essentials to
        Luxury Finds, Our Product Range Has Something for Everyone!
      </p>
    </div>

    <div
      class="mt-16 grid lg:grid-cols-4 md:grid-cols-3 sm:grid-cols-2 grid-cols-1 gap-14 sm:gap-4"
    >
      <PopularProductsCard
        v-for="product in products"
        :key="product.id"
        :product="products[product.id]"
      />
    </div>
  </section>
</template>

<script setup>
import PopularProductsCard from "@/components/PopularProductsCard.vue";
import { products } from "@/constants";
</script>
