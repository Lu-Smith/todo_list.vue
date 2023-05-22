<template>
  <h2>Things to do 🤔</h2>
  <div v-for="task in tasks" :key="task">
    <p>{{ task }}</p>
  </div>
</template>

<script>
export default {
  props: ["tasks"]
}
</script>

<style>

</style>