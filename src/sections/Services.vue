<template>
  <section class="max-container flex justify-center flex-wrap gap-9">
    <ServiceCard
      v-for="service in services"
      :key="service.id"
      :service="services[service.id]"
    />
  </section>
</template>

<script setup>
import { ServiceCard } from "@/components";
import { services } from "@/constants";
</script>
