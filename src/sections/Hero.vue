<template>
  <section
    id="home"
    class="w-full flex flex-col xl:flex-row gap-10 justify-center min-h-screen max-container"
  >
    <div
      class="relative w-full xl:w-2/5 flex flex-col justify-center items-start max-xl:padding-x pt-28 z-20"
    >
      <p class="capitalize text-xl font-montserrat text-coral-red">
        our summer collections
      </p>

      <h1
        class="capitalize mt-10 font-palanquin text-8xl font-bold max-sm:text-[72px] max-sm:leading-[82px]"
      >
        <span
          class="max-xl:bg-white max-xl:whitespace-nowrap relative z-10 pr-10"
          >the new arrival</span
        >
        <br />
        <span class="text-coral-red inline-block mt-3">nike</span> shoes
      </h1>

      <p
        class="font-montserrat text-slate-gray text-lg leading-8 mt-6 mb-14 sm:max-w-sm"
      >
        Discover stylish Nike arrivals, quality comfort, and innovation for your
        active life.
      </p>

      <btn label="Shop Now" :iconURL="arrowRight" />

      <div class="flex justify-start items-start flex-wrap w-full mt-20 gap-16">
        <div v-for="stat in statistics" :key="stat.id">
          <p class="text-4xl font-palanquin font-bold">{{ stat.value }}</p>
          <p class="leading-7 font-montserrat text-slate-gray">
            {{ stat.label }}
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { btn } from "@/components";
import { arrowRight } from "@/assets/icons";
import { statistics } from "@/constants";
</script>
