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
header {
  text-align: center;
}
header .order {
  margin-top: 20px;
}
button {
  margin: 0 10px;
  color: #1195c9;
  border: 3px solid #1195c9;
  background: #d5f0ff;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}
</style>
