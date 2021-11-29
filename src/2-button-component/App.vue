<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <HelloWorld msg="Welcome to Your Vue.js + TypeScript App" />
  <Button label="Click me" :show="true" @event="buttonEvent" />
  <ResettableInput />
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import Button from './components/Button.vue'
import ResettableInput from './components/ResettableInput.vue'
import HelloWorld from './components/HelloWorld.vue'

export default defineComponent({
  name: 'App',
  components: {
    Button,
    ResettableInput,
    HelloWorld,
  },
  setup() {
    const buttonEvent = () => {
      alert('Button event received at app')
    }

    return {
      buttonEvent,
    }
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
