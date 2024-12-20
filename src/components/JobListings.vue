<template>
  <section class="px-10 py-10 bg-green-50">
    <h2 class="text-3xl font-bold text-center text-green-500 mb-6">
      Browse Jobs
    </h2>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
      <JobListing
        v-for="job in jobs.slice(0, limit || jobs.length)"
        :key="job.id"
        :job="job"
        :limit="limit"
      />
    </div>
    <section v-if="showViewAllBtn" class="m-auto max-w-lg my-10 px-6">
      <a
        :href="'/jobs'"
        class="block bg-black text-white text-center py-4 px-6 rounded-xl hover:bg-gray-700"
        >View All Jobs</a
      >
    </section>
  </section>
</template>

<script setup>
import { defineProps, ref } from "vue";
import jobData from "../jobs.json";
import JobListing from "./JobListing.vue";

const jobs = ref(jobData.jobs);
defineProps({
  limit: {
    type: Number,
  },
  showViewAllBtn: {
    type: Boolean,
    default: false,
  },
});
</script>
