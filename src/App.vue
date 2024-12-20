<script lang="ts">
import { defineComponent, ref } from "vue";
import JobList from "./components/JobList.vue";

import job from "./types/Job";

export default defineComponent({
  name: "App",
  components: { JobList },
  setup() {
    const jobHunts = ref<job[]>([
      {
        title: "Software Engineer",
        id: 1,
        salary: 85000,
        location: "San Francisco, CA",
      },
      {
        title: "Data Scientist",
        id: 2,
        salary: 95000,
        location: "New York, NY",
      },
      {
        title: "Product Manager",
        id: 3,
        salary: 105000,
        location: "Seattle, WA",
      },
      {
        title: "UX Designer",
        id: 4,
        salary: 75000,
        location: "Austin, TX",
      },
    ]);

    return { jobHunts };
  },
});
</script>

<template>
  <div class="app">
    <JobList :jobHunts="jobHunts" />
  </div>
</template>

<style></style>
