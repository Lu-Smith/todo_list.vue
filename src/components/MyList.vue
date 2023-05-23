<template>
  <h2>Things to do 🤔</h2>
  <div v-for="task in tasks" :key="task">
      <div @click="markDoneTask(task)" :class="{'task': true, 'done-task': task.done}">
        <p>{{ task.name }}</p>
        <button @click="removeTask(task)">remove</button>
      </div>
  </div>
</template>

<script>
export default {
  props: ["tasks"],
  methods: {
    markDoneTask(task) {
      task.done = !task.done;
    },
    removeTask(task) {
      this.$emit("remove-task", task)
    }
  }
}
</script>

<style>
.task {
  background: black;
  color: white;
  margin: 5px auto;
  padding: 10px;
  border: 2px solid red;
  border-radius: 40px;
  width: 80%;
}

.done-task {
  background: blue;
}
</style>