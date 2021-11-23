<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <HelloWorld msg="Welcome to Your Vue.js + TypeScript App" />
  <Button name="Click Me!" @action="action" />
  <Clock :fontColor="clockColor" />
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import Clock from './components/Clock.vue'
import Button from './components/Button.vue'
import HelloWorld from './components/HelloWorld.vue'

export default defineComponent({
  name: 'App',
  components: {
    Clock,
    Button,
    HelloWorld,
  },
  setup() {
    const clockColor = ref('#41b883')
    const action = () => {
      clockColor.value = clockColor.value === '#41b883' ? '#2c3e50' : '#41b883'
    }

    return { action, clockColor }
  },
})
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
