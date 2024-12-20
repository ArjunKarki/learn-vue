<template>
  <section class="px-4 py-10 bg-green-10">
    <h2 class="text-3xl font-bold text-center text-green-500 mb-6">
      Browse Jobs
    </h2>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
      <div v-for="job in jobs" :key="job.id">
        <JobListing />
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from "vue";
import jobData from "../jobs.json";
import JobListing from "./JobListing.vue";

const jobs = ref(jobData.jobs);
</script>
