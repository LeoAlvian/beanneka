<template>
  <!-- <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </nav>
  <router-view/> -->
  <SideBar/>
  <div class="main-pannel" :style="{ 'margin-left' : sidebarWidth }">
    <router-view />
  </div>
</template>

<script>

import SideBar from './components/sidebar/SideBar.vue'
import { sidebarWidth } from './components/sidebar/State'

export default {
  components: {SideBar},
  setup () {
    return { sidebarWidth }
  }
}
</script>

<style>

* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

body {
  background-color: var(--blue2);
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.main-pannel {
  transition: 0.4s ease-in-out;
}
</style>
