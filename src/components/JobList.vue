<script lang="ts">
import { defineComponent, PropType } from "vue";
import Job from "@/types/Job";

export default defineComponent({
  name: "JobList",
  component: [],
  props: {
    jobHunts: {
      required: true,
      type: Array as PropType<Job[]>,
    },
  },
});
</script>

<template>
  <div class="job-list">
    <ul>
      <li v-for="job in jobHunts" :key="job.id">
        <h2>{{ job.title }} in {{ job.location }}</h2>
        <div>$ {{ job.salary }}</div>
        <div class="description">
          Lorem ipsum, dolor sit amet consectetur adipisicing elit. Facilis
          neque harum reiciendis sapiente dolores vitae molestiae quasi amet
          accusamus dolor?
        </div>
      </li>
    </ul>
  </div>
</template>
<style scoped></style>
