<template>
    <div class="home">
      <h1>home</h1>
      <input type="text" placeholder="enter the task..." v-model="task" >
      <button @click="addTask">add</button>
      <MyList :tasks="tasks" />
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
      task: ""
    }
  },
  methods: {
    addTask() {
      this.tasks.push(this.task)
    }
  }
}
</script>
