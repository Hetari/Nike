<template>
  <section
    id="home"
    class="w-full flex flex-col xl:flex-row gap-10 justify-center min-h-screen max-container"
  >
    <div
      class="relative w-full xl:w-2/5 flex flex-col justify-center items-start max-xl:padding-x pt-28 z-20 max-lg:pt-44 max-sm:pt-36"
    >
      <p
        class="capitalize text-xl max-sm:text-lg font-montserrat text-coral-red"
      >
        our summer collections
      </p>

      <h1 class="heading-title">
        <span
          class="inline-block xl:bg-white xl:whitespace-nowrap relative z-10 pr-10"
          >the new arrival</span
        >
        <br />
        <span class="text-coral-red inline-block">nike</span> shoes
      </h1>

      <p class="info-text mt-6 mb-14 sm:max-w-sm">
        Discover stylish Nike arrivals, quality comfort, and innovation for your
        active life.
      </p>

      <btn label="Shop Now" :iconURL="arrowRight" link="#products" />

      <div
        class="flex justify-start items-start flex-wrap w-full mt-20 gap-16 max-sm:gap-0"
        id="counts"
      >
        <div v-for="stat in statistics" :key="stat.id">
          <p
            id="count"
            :data-counter="stat.value"
            class="text-4xl font-palanquin font-bold max-sm:text-2xl"
            style="width: 100px"
          >
            0
          </p>
          <p class="info-text">
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
        <div class="img-hover odd:alt" v-for="shoe in shoes" :key="shoe.id">
          <ShoeCard
            :imgURL="shoe"
            :bigShoeImage="currentShoe"
            :isHero="true"
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

const preloadImages = () => {
  return new Promise((resolve, reject) => {
    const imagePromises = shoes.map((shoe) => {
      return Promise.all([
        new Promise((resolve, reject) => {
          const thumbnailImg = new Image();
          thumbnailImg.onload = resolve;
          thumbnailImg.onerror = reject;
          thumbnailImg.src = shoe.thumbnail;
        }),
        new Promise((resolve, reject) => {
          const bigShoeImg = new Image();
          bigShoeImg.onload = resolve;
          bigShoeImg.onerror = reject;
          bigShoeImg.src = shoe.bigShoe;
        }),
      ]);
    });

    Promise.all(imagePromises.flat())
      .then(() => {
        resolve(); // Resolve the main promise when all images are preloaded
      })
      .catch((error) => {
        reject(error); // Reject the main promise if there's an error
      });
  });
};

onMounted(async () => {
  try {
    await preloadImages();
    document.querySelectorAll("[data-counter]").forEach(counter);
  } catch (error) {
    console.error("Error:", error);
  }
});
</script>
