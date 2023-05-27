<template>
  <transition name="switch">
    <h2 v-if="tasks.length > 0">{{ listTitle }}</h2>
    <h2 v-else>Woohoo, nothing to do!</h2>
  </transition>
  <transition-group tag="div" name="list" appear>
    <div v-for="task in tasks" :key="task.id">
        <div :class="{'task': true, 'done-task': task.done}">
          <span>{{ task.id }}</span>
          <span v-if="task.done" class="material-symbols-outlined done-tick" >
            done
          </span>
          <span @click="markDoneTask(task)" class="task-name">{{ task.name }}</span>
          <button @click="removeTask(task)" class="bin"><span class="material-symbols-outlined">
            delete
          </span>
          </button>
        </div>
    </div>
  </transition-group>
</template>

<script>
export default {
  props: ["tasks"],
  data() {
    return {
      listTitle: 'My List 📃'
    }
  },
  methods: {
    markDoneTask(task) {
      task.done = !task.done;
    },
    removeTask(task) {
      this.$emit("remove-task", task)
      console.log(task.done);
    }
  },
  emits: ['remove-task', 'update-tasks']
}
</script>

<style>
.task {
  background: black;
  color: white;
  margin: 5px auto;
  padding: 10px 30px;
  border: 2px solid red;
  border-radius: 40px;
  width: 80%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  box-shadow: 3px 3px 3px rgba(0, 0, 0, 0.2);
  letter-spacing: 1px;
  font-size: 20px;
}

.task-name {
  width: 65%;
}

.bin {
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

.done-tick {
  color:rgb(65, 230, 32);
}

.list-enter-from {
  opacity: 0;
  transform: scale(0.6);
}

.list-enter-to {
  opacity: 1;
  transform: scale(1);
}

.list-enter-active, .list-leave-active {
  transition: all 0.4s ease;
}

.list-leave-from {
  opacity: 1;
  transform: scale(1);
}

.list-leave-to {
  opacity: 0;
  transform: scale(0.6);
}

</style>