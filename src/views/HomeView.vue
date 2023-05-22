<template>
    <div class="home">
      <h1>home</h1>
      <input type="text" placeholder="enter the task..." v-model="task">
      <p>{{ task }}</p>
      <MyList />
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
      task: ""
    }
  }
}
</script>
