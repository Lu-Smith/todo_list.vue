<template>
  <h2>Things to do 🤔</h2>
  <div v-for="task in tasks" :key="task">
      <div @click="markDoneTask(task)" :class="{'task': true, 'doneTask': doneTask}">
        <p>{{ task }}</p>
        <button @click="removeTask(task)">remove</button>
      </div>
  </div>
</template>

<script>
export default {
  props: ["tasks"],
  data () {
    return {
      doneTask: false
    }
  },
  methods: {
    markDoneTask(task) {
        this.doneTask = !this.doneTask
    },
    removeTask(task) {
      this.tasks = this.tasks.filter((item) => item !== task )
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