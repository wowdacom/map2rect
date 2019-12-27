<template>
  <div id="app">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <GetMap></GetMap>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import GetMap from './components/GetMap.vue'

export default {
  name: 'app',
  components: {
    HelloWorld,
    GetMap
  }
}
</script>

<style lang="scss">
#app {

}
</style>
