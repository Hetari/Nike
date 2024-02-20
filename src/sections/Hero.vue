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
          <p
            id="count"
            :data-counter="stat.value"
            class="text-4xl font-palanquin font-bold"
          >
            0
          </p>
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
import { onMounted, ref } from "vue";

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

const formatNumber = (num) => {
  // Suffixes for thousands, millions, billions, trillions, etc.
  const suffixes = ["", "K", "M", "B", "T"];

  // Determine the magnitude (which suffix to use)
  let magnitude = Math.floor(Math.log10(Math.abs(num)) / 3);

  // Ensure we don't go beyond available suffixes
  magnitude = Math.min(magnitude, suffixes.length - 1);

  // Adjust number to appropriate magnitude
  const rounded = num / Math.pow(10, magnitude * 3);

  // Return formatted number with appropriate suffix
  return rounded.toFixed(1) + suffixes[magnitude];
};

// https://stackoverflow.com/questions/70746105/animate-counter-from-start-to-end-value#answer-70746179
const counter = (EL) => {
  // Animate all counters equally for a better UX
  const duration = 2500;

  // Get start and end values
  const start = parseInt(EL.textContent, 10);

  // PS: Use always the radix 10!
  const end = parseInt(EL.dataset.counter, 10);
  4;

  // If equal values, stop here.
  if (start === end) return;

  // Get the range
  const range = end - start;

  // Set current at start position
  let curr = start;

  const timeStart = Date.now();

  const loop = () => {
    let elaps = Date.now() - timeStart;

    // Stop the loop
    if (elaps > duration) elaps = duration;

    // Get the time fraction
    const frac = elaps / duration;

    // Calculate the value step
    const step = frac * range;

    // Increment or Decrement current value
    curr = start + step;

    // Apply to UI as integer
    EL.textContent = formatNumber(Math.trunc(curr));

    // Loop
    if (elaps < duration) requestAnimationFrame(loop);
  };

  // Start the loop!
  requestAnimationFrame(loop);
};

onMounted(() => {
  document.querySelectorAll("[data-counter]").forEach(counter);
});
</script>