<script lang="ts">
import { computed, defineComponent, PropType } from "vue";
import Job from "@/types/Job";
import OrderTerm from "@/types/OrderTerm";

export default defineComponent({
  name: "JobList",
  component: [],
  props: {
    jobHunts: {
      required: true,
      type: Array as PropType<Job[]>,
    },
    order: {
      required: true,
      type: String as PropType<OrderTerm>,
    },
  },

  setup(props) {
    const orderJobs = computed(() => {
      return [...props.jobHunts].sort((a: Job, b: Job) => {
        return a[props.order] > b[props.order] ? 1 : -1;
      });
    });

    return { orderJobs };
  },
});
</script>

<template>
  <div class="job-list">
    <div>
      {{ order }}
    </div>
    <ul>
      <li v-for="job in orderJobs" :key="job.id">
        <h2>{{ job.title }} in {{ job.location }}</h2>
        <div class="salary">
          <span>$ </span>
          <p>{{ job.salary }}</p>
        </div>
        <div class="description">
          {{ job.description }}
        </div>
      </li>
    </ul>
  </div>
</template>
<style scoped>
.job-list {
  max-width: 960px;
  margin: 40px auto;
}
.job-list ul {
  padding: 0;
}
.job-list li {
  list-style-type: none;
  background: white;
  padding: 16px;
  margin: 16px 0;
  border-radius: 4px;
}
.job-list h2 {
  margin: 0 0 10px;
  text-transform: capitalize;
}
.salary {
  display: flex;
  justify-content: start;
  align-items: center;
}
.salary img {
  width: 30px;
}
.salary p {
  /* color: #17bf66; */
  color: red;
  font-weight: bold;
  margin: 10px 4px;
}
</style>
