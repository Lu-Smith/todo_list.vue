<template>
  <h2>Things to do 🤔</h2>
  <div v-for="task in tasks" :key="task">
      <div @click="markDoneTask(task)" :class="{'task': true, 'done-task': task.done}">
        <span>{{ task.name }}</span>
        <button @click="removeTask(task)"><span class="material-symbols-outlined">
delete
</span></button>
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
  display: flex;
  align-items: center;
  justify-content: space-between;
}

button {
  background: none;
  border: none;
}

.material-symbols-outlined {
  color: white;
  font-variation-settings:
  'FILL' 10,
  'wght' 800,
  'GRAD' 100,
  'opsz' 28
}

.done-task {
  background: rgb(240, 96, 151);
  width: 50%;
}
</style>