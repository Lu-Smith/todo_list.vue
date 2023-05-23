<template>
    <div class="home">
      <h1>home</h1>
      <input type="text" placeholder="enter the task..." v-model="tempTask" >
      <button @click="addTask" class="addTaskButton">add</button>
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
      if (this.tempTask.length > 2) {
        this.tasks.push({name: this.tempTask, done: false})
      }
      
      this.tempTask = ""
    },
    removeTask(task) {
      this.tasks = this.tasks.filter(item => item !== task);
    }
  }
}
</script>

<style>
input {
  background: rgb(248, 244, 244);
  color: rgb(99, 6, 6);
  padding: 10px;
  border: none;
  border-top: 2px solid red;
  border-left: 2px solid red;
  border-bottom: 2px solid red;
  border-top-left-radius: 40px;
  border-bottom-left-radius: 40px;
  width: 40%;
}

.addTaskButton {
  background: rgb(102, 4, 4);
  color: white;
  padding: 10px 30px 10px 20px;
  border: none;
  border-top: 2px solid red;
  border-right: 2px solid red;
  border-bottom: 2px solid red;
  border-top-right-radius: 40px;
  border-bottom-right-radius: 40px;
  cursor: pointer;
}
</style>
