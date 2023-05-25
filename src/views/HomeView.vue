<template>
    <div class="home">
      <h1>What to do today 🤔</h1>
      <div  class="error" :class="{'show-error' : showError}">You must enter a task ( more than 2 characters ).</div>
      <input type="text" placeholder="enter the task..." v-model="tempTask" @keydown.enter="addTask"/>
      <button @click="addTask" class="addTaskButton">add</button>
      <MyList :tasks="tasks" @remove-task="removeTask" />
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
      tempTask: "",
      showError: false,
      id: 1
    }
  },
  methods: {
    addTask() {
      if (this.tempTask.length > 2) {
        this.tasks.push({name: this.tempTask, done: false, id: this.id++})
        this.showError = false
      } else {
        this.showError = true
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
  padding: 10px 30px;
  border: none;
  border-top: 2px solid red;
  border-left: 2px solid red;
  border-bottom: 2px solid red;
  border-top-left-radius: 40px;
  border-bottom-left-radius: 40px;
  width: 40%;
  box-shadow: 3px 3px 3px rgba(0, 0, 0, 0.2);
  font-size: 18px;
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
  box-shadow: 3px 3px 3px rgba(0, 0, 0, 0.2);
  font-size: 18px;
}

.error {
  background: red;
  padding: 20px 30px;
  color: white;
  position: fixed;
  top: 30px;
  left: 0px;
  right: 0px;
  width: 60%;
  margin: auto;
  border-radius: 20px;
  display: none;
}

.show-error {
  display: block;
}
</style>
