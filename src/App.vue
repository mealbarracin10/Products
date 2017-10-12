<template>
  <div id="app">
    <hello-world/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'

export default {
  name: 'app',
  components: {
    HelloWorld
  }
}
</script>

<style>
img.logo {
  width: 50px;
  float: left;
  margin-right: 15px;
}
</style>
