<template>
  <section class="max-container">
    <h3 class="heading-title">
      what our <span class="text-coral-red">customers</span> say?
    </h3>
    <p className="info-text  mt-4 max-w-lg ">
      Hear genuine stories from our satisfied customers about their exceptional
      experiences with us.
    </p>
    <div
      className="mt-24 flex flex-1 justify-evenly items-center max-lg:flex-col gap-14"
    >
      <ReviewCard
        v-for="review in reviews"
        :key="review.id"
        :review="reviews[review.id]"
      />
    </div>
  </section>
</template>

<script setup>
import ReviewCard from "@/components/ReviewCard.vue";
import { reviews } from "@/constants";
</script>
