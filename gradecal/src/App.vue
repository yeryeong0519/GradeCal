<!-- src/App.vue -->
<template>
  <div id="app">
    <h1 class="title">Front-end 과제</h1>
    <Table />
  </div>
</template>

<script>
import Table from "@/components/GradeCal.vue";

export default {
  components: {
    Table,
  },
};
</script>

<style>
/* Add your global styles here */

.title {
  text-align: center;
  margin-top: 20px;
}
</style>
