<template>
    <div class="home">
      <h1>home</h1>
      <input type="text" placeholder="enter the task..." v-model="tasks" >
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
      tasks: ""
    }
  },
  methods: {
    addTask() {
      console.log(this.tasks)
    }
  }
}
</script>
