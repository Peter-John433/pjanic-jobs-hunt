<script lang="ts">
import { defineComponent, ref } from "vue";
import JobList from "./components/JobList.vue";
import OrderTerm from "./types/OrderTerm";

import job from "./types/Job";

export default defineComponent({
  name: "App",
  components: { JobList },
  setup() {
    const jobHunts = ref<job[]>([
      {
        title: "Software Engineer",
        id: 1,
        salary: 90000,
        location: "San Francisco, CA",
        description:
          "Designs, develops, and maintains software applications while collaborating with cross-functional teams.",
      },
      {
        title: "Data Scientist",
        id: 2,
        salary: 100000,
        location: "New York, NY",
        description:
          "Analyzes large datasets to uncover trends and insights, supporting data-driven decision-making.",
      },
      {
        title: "Product Manager",
        id: 3,
        salary: 110000,
        location: "Seattle, WA",
        description:
          "Leads product development, coordinates with stakeholders, and ensures alignment with company goals.",
      },
      {
        title: "UX Designer",
        id: 4,
        salary: 80000,
        location: "Austin, TX",
        description:
          "Creates intuitive designs to enhance user experience and improve product usability.",
      },
      {
        title: "DevOps Engineer",
        id: 5,
        salary: 95000,
        location: "Denver, CO",
        description:
          "Maintains and improves development workflows, ensuring continuous integration and delivery pipelines.",
      },
      {
        title: "QA Analyst",
        id: 6,
        salary: 70000,
        location: "Chicago, IL",
        description:
          "Tests software applications to identify bugs, ensure quality, and maintain performance standards.",
      },
    ]);

    const order = ref<OrderTerm>("title");

    //handleorder func
    const handleOrder = (orderTerm: OrderTerm) => {
      order.value = orderTerm;
    };

    return { jobHunts, order, handleOrder };
  },
});
</script>

<template>
  <div class="app">
    <div class="heart">
      <img src="@/assets/heart.svg" alt="heart" />
      <h1>Job Hunts</h1>
    </div>
    <header>
      <div class="order">
        <button @click="handleOrder('title')">title</button>
        <button @click="handleOrder('salary')">salary</button>
        <button @click="handleOrder('location')">location</button>
      </div>
    </header>
    <JobList :jobHunts="jobHunts" :order="order" />
  </div>
</template>

<style scoped>
.heart {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 10px;
}

.heart img {
  width: 50px;
  object-fit: contain;
}

header {
  text-align: center;
}
header .order {
  margin-top: 20px;
}
button {
  margin: 0 10px;
  color: white;
  border: 3px solid #008000;
  background: #1be21b;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
  font-style: normal;
  width: 100px;
}
</style>
