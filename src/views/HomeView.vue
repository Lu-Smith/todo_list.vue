<template>
    <div class="home">
      <h1>home</h1>
      <input type="text" placeholder="enter the task..." v-model="tempTask" >
      <button @click="addTask">add</button>
      <MyList :tasks="tasks" @remove-task="removeTask"/>
    </div>
</template>

<script>
import MyList from '@/components/MyList.vue';

export default {
  name: 'HomeView',
  components: {
    MyList
  },
  data () {
    return {
      tasks: [],
      tempTask: ""
    }
  },
  methods: {
    addTask() {
      this.tasks.push({name: this.tempTask, done: false})
      this.tempTask = ""
    },
    removeTask(task) {
      this.tasks = this.tasks.filter(item => item !== task);
    }
  }
}
</script>
