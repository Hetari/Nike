<template>
  <header
    class="padding-x py-8 z-10 w-full"
    :class="{
      'relative h-[100svh]': isVisible,
    }"
  >
    <nav
      class="flex justify-between items-center max-container"
      :class="{
        'flex-col': isVisible,
      }"
    >
      <a
        href="/"
        :class="{
          'w-full justify-start': isVisible,
        }"
      >
        <img :src="headerLogo" alt="Logo" width="130" height="29" />
      </a>

      <ul
        class="flex flex-1 justify-center items-center gap-16"
        :class="{
          'flex-col absolute top-8 right-8 gap-8': isVisible,
          'max-lg:hidden': !isVisible,
        }"
      >
        <div class="flex justify-end w-full">
          <img
            :src="closeHamburger"
            alt="Hamburger"
            width="50"
            height="50"
            class="cursor-pointer"
            v-if="isVisible"
            @click="toggleNav"
          />
        </div>
        <li
          v-for="navLink in navLinks"
          :key="navLink.label"
          :class="{
            'w-full text-end': isVisible,
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
      <div
        class="hidden max-lg:block cursor-pointer p-5 -m-5"
        @click="toggleNav"
      >
        <img
          :src="hamburger"
          alt="Hamburger"
          width="50"
          height="50"
          v-if="!isVisible"
        />
      </div>
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
