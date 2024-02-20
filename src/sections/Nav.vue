<template>
  <header
    class="padding-x py-8 w-full absolute inset-0 h-screen"
    :class="{
      ' h-[100svh] relative': isVisible,
    }"
  >
    <nav class="flex justify-between items-center max-container">
      <a
        href="/"
        class="z-50"
        :class="{
          'w-full justify-start pt-[3.5px]': isVisible,
        }"
      >
        <img :src="headerLogo" alt="Logo" width="130" height="29" />
      </a>
      <div
        class="cursor-pointer p-5 -m-5 z-50"
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
        class="flex flex-1 justify-center items-center gap-16 z-50"
        :class="{
          'flex-col justify-between absolute top-24 right-10  gap-4 ':
            isVisible,
          'max-lg:hidden': !isVisible,
        }"
      >
        <li
          v-for="navLink in navLinks"
          :key="navLink.label"
          class="rounded text-center hover:bg-coral-red group transition-all"
          :class="{
            'w-[85vw] text-end': isVisible,
          }"
        >
          <a
            :href="navLink.href"
            class="font-montserrat leading-normal text-lg text-slate-gray group-hover:text-white py-3 px-5"
            :class="{ 'ps-0 pe-5': isVisible }"
            >{{ navLink.label }}</a
          >
        </li>
      </ul>
    </nav>
  </header>
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
