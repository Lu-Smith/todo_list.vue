<template>
  <h2>Things to do 🤔</h2>
  <div v-for="task in tasks" :key="task">
    <div @clicremoveTaskk="(task)" class="task">{{ task }}</div>
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
    removeTask(task) {
       console.log(task)
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
</style>