<template>
  <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
    <router-link to="/contact">Contact</router-link>
  </nav>
  <router-view/>
  <MainFooter />
</template>

<script>
import MainFooter from '@/components/MainFooter.vue';

export default {
  name: 'HomeView',
  components: {
    MainFooter
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
  background: black;
}

nav a {
  font-weight: bold;
  color: #f6f8fa;
  margin: 5px;
  letter-spacing: 1px;
}

nav a.router-link-exact-active {
  color:  rgb(247, 27, 27);
}

h1 {
    margin-top: 50px;
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
</style>
