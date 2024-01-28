<template>
  <header>
    <h1 class="text-5xl text-red-900">hi</h1>
    <div class="wrapper">
      <nav></nav>
    </div>
  </header>

  <RouterView />
</template>

<script setup>
import { RouterLink, RouterView } from "vue-router";
</script>
