<template>
  <section
    id="home"
    class="padding-x w-full flex flex-col xl:flex-row gap-10 justify-center min-h-screen max-container"
  >
    <div
      class="relative w-full xl:w-2/5 flex flex-col justify-center items-start max-xl:padding-x pt-28 z-20 max-lg:pt-44"
    >
      <p class="capitalize text-xl font-montserrat text-coral-red">
        our summer collections
      </p>

      <h1
        class="capitalize mt-10 font-palanquin text-8xl font-bold max-sm:text-[72px] max-sm:leading-[82px]"
      >
        <span class="xl:bg-white xl:whitespace-nowrap relative z-10 pr-10"
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
    <div
      class="relative flex flex-1 justify-center items-center xl:min-h-screen max-xl:py-40 bg-primary bg-center bg-hero bg-cover"
    >
      <img
        :src="currentShoe"
        alt="shoe collection"
        width="610"
        height="500"
        class="object-contain relative z-10"
        :ref="shoeHero"
      />
      <div
        class="flex sm:gap-6 gap-4 absolute -bottom-[5%] sm:left-[10%] max-sm:px-6 z-10"
      >
        <div v-for="shoe in shoes" :key="shoe.id">
          <ShoeCard
            :imgURL="shoe"
            :bigShoeImage="currentShoe"
            @changeBigShoeImage="changeBigShoeImage"
          />
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { btn, ShoeCard } from "@/components";
import { arrowRight } from "@/assets/icons";
import { statistics, shoes } from "@/constants";
import { bigShoe1 } from "@/assets/images";
import { ref } from "vue";

let currentShoe = ref(bigShoe1); // Initialize currentShoe as a ref
let shoeHero = ref(null); // Define the ref for the image element

function changeBigShoeImage(val) {
  currentShoe.value = val;
  updateShoeImage();
}

// Function to update the image source
function updateShoeImage() {
  const imgElement = ref.shoeHero; // Access the image element using the ref
  if (imgElement) {
    imgElement.src = currentShoe.value; // Update the src attribute
  }
}
</script>
