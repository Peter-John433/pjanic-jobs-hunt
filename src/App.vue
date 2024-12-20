<template>
  <h1>{{ hello }}</h1>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";

export default defineComponent({
  components: {},
  setup() {
    const hello = ref<string>("hello world");

    return { hello };
  },
});
</script>

<style></style>
