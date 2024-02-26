<template>
  <footer class="max-container">
    <div
      class="flex justify-between items-start gap-20 flex-wrap max-lg:flex-col"
    >
      <div class="flex flex-1 justify-start flex-col items-stretch">
        <a href="/">
          <img :src="footerLogo" alt="logo" width="150" height="46" />
        </a>
        <p
          class="mt-6 text-base leading-7 font-montserrat text-white-400 sm:max-w-sm"
        >
          Get shoes ready for the new term at your nearest Nike store. Find Your
          perfect Size In Store. Get Rewards
        </p>
        <div class="flex justify-start items-center gap-5 my-8">
          <div
            class="flex justify-center items-center size-12 bg-white rounded-full"
            v-for="social in socialMedia"
            :key="social.id"
          >
            <img :src="social.src" :alt="social.alt" width="24" height="24" />
          </div>
        </div>

        <div class="flex flex-1 justify-between lg:gap-10 gap-20 flex-wrap">
          <div v-for="section in footerLinks" :key="section.title">
            <h4
              class="font-montserrat text-2xl leading-normal font-medium mb-6 text-white"
            >
              {{ section.title }}
            </h4>
            <ul>
              <li
                v-for="link in section.links"
                class="mt-3 font-montserrat text-base leading-normal text-white-400 hover:text-slate-gray"
                :key="link.name"
              >
                <a :href="link.link">{{ link.name }}</a>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
    <div
      class="flex justify-between text-white-400 mt-24 max-sm:flex-col max-sm:items-center"
    >
      <div
        class="flex flex-1 justify-start items-center gap-2 font-montserrat cursor-pointer"
      >
        <img
          :src="copyrightSign"
          alt="copyright sign"
          width="20"
          height="20"
          class="rounded-full m-0"
        />
        <p>Copyright. All rights reserved.</p>
      </div>
      <p class="font-montserrat cursor-pointer">Terms & Conditions</p>
    </div>
  </footer>
</template>

<script setup>
import { copyrightSign } from "@/assets/icons";
import { footerLogo } from "@/assets/images";
import { socialMedia, footerLinks } from "@/constants";
</script>
