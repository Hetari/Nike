<template>
  <header
    class="padding-x py-8 z-10 w-full relative"
    :class="{
      ' h-[100svh]': isVisible,
    }"
  >
    <nav class="flex justify-between items-center max-container">
      <a
        href="/"
        :class="{
          'w-full justify-start pt-[10.5px]': isVisible,
        }"
      >
        <img :src="headerLogo" alt="Logo" width="130" height="29" />
      </a>
      <div
        class="cursor-pointer p-5 -m-5"
        :class="{
          'none max-lg:block': !isVisible,
        }"
        @click="toggleNav"
      >
        <img
          :src="hamburger"
          alt="Hamburger"
          width="50"
          height="50"
          v-if="!isVisible"
        />
        <img
          :src="closeHamburger"
          alt="Hamburger"
          width="50"
          height="50"
          v-if="isVisible"
        />
      </div>

      <ul
        class="flex flex-1 justify-center items-center gap-16"
        :class="{
          'flex-col justify-between absolute top-24 right-16 gap-8 ': isVisible,
          'max-lg:hidden': !isVisible,
        }"
      >
        <li
          v-for="navLink in navLinks"
          :key="navLink.label"
          :class="{
            'w-full  text-end': isVisible,
          }"
        >
          <a
            :href="navLink.href"
            class="font-montserrat leading-normal text-lg text-slate-gray"
            >{{ navLink.label }}</a
          >
        </li>
      </ul>

      <!-- </div> -->
    </nav>
  </header>
  <!-- <div>
    <RouterView />
  </div> -->
</template>

<script setup>
import { ref } from "vue";
import { headerLogo } from "@/assets/images";
import { hamburger, closeHamburger } from "@/assets/icons";
import { navLinks } from "@/constants";

let isVisible = ref(false);
function toggleNav() {
  isVisible.value = !isVisible.value;
}
</script>
