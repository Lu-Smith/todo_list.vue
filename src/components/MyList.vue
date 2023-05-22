<template>
  <h2>Things to do 🤔</h2>
  <div v-for="task in tasks" :key="task">
    <p @click="removeTask(task)">{{ task }}</p>
  </div>
</template>

<script>
export default {
  props: ["tasks"],
  methods: {
    removeTask(task) {
       console.log(task)
    }
  }
}
</script>

<style>

</style>