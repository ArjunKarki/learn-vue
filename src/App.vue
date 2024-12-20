<template>
  <Navbar />
  <Hero />
  <HomeCard />
  <JobListings :limit="3" :show-view-all-btn="true" />
</template>

<script setup>
import Hero from "./components/Hero.vue";
import HomeCard from "./components/HomeCard.vue";
import JobListings from "./components/JobListings.vue";
import Navbar from "./components/Navbar.vue";
</script>
