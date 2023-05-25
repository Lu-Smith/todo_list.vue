<template>
    <div class="home">
      <h1>What to do today 🤔</h1>
      <div  class="error" :class="{'show-error' : showError}">You must enter a task ( more than 2 characters ).</div>
      <input type="text" placeholder="enter the task..." v-model="tempTask" @keydown.enter="addTask"/>
      <button @click="addTask" class="addTaskButton">add</button>
      <MyList :tasks="tasks" @remove-task="removeTask" @update-tasks="updateTasks" />
      <transition name="fade">
        <div v-if="showP" class="fun-phrase">hello, sunshine 🌞</div>
      </transition>
      <button class="toggle-button" @click="showP = !showP">toggle</button>
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
      id: 1,
      showP: false
    }
  },
  methods: {
    addTask() {
      if (this.tempTask.length > 2) {
        this.tasks.push({name: this.tempTask, done: false, id: this.id++})
        this.showError = false
        this.updateTaskIDs();
      } else {
        this.showError = true
      }
       
      this.tempTask = ""
    },
    removeTask(task) {
      this.tasks = this.tasks.filter(item => item !== task);
      this.updateTaskIDs();
    },
    updateTaskIDs() {
      this.tasks.forEach((task, index) => {
        task.id = index + 1;
      });
      this.$emit('update-tasks', this.tasks);
    },
    updateTasks(updatedTasks) {
      this.tasks = updatedTasks;
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

button {
  background: rgb(102, 4, 4);
  color: white;
  padding: 10px 20px;
  border: none;
  cursor: pointer;
  font-size: 18px;
  border-radius: 20px;
}

.toggle-button {
  position: fixed;
  bottom: 100px;
}

.addTaskButton {
  border-top-left-radius: 0;
  border-bottom-left-radius: 0;
  padding: 10px 30px 10px 20px;
  border-top: 2px solid red;
  border-right: 2px solid red;
  border-bottom: 2px solid red;
  border-top-right-radius: 40px;
  border-bottom-right-radius: 40px;
  box-shadow: 3px 3px 3px rgba(0, 0, 0, 0.2);
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

.fun-phrase {
  margin-bottom: 10px;
}

.fade-enter-from {
  opacity: 0;
}

.fade-enter-to {
  opacity: 1;
}

.fade-enter-active, .fade-leave-active {
  transition: all 2s ease;
}

.fade-leave-from {
  opacity: 1;
}

.fade-leave-to {
  opacity: 0;
}
</style>
