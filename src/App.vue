<template>
  <div id="app">
    <Piano/>
  </div>
</template>

<script>
import Piano from './components/Piano.vue'
import Vue from 'vue';
import VueKonva from 'vue-konva'

Vue.use(VueKonva)

export default {
  name: 'App',
  components: {
    Piano
  }
}
</script>

<style>

</style>
