<template>
    <div class="home">
      <h1>home</h1>
      <input type="text">
      <MyList />
    </div>
</template>

<script>
import MyList from '@/components/MyList.vue';

export default {
  name: 'HomeView',
  components: {
    MyList
  }
}
</script>
