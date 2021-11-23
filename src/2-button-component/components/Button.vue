<template>
  <div>
    <button @click="clickAction">{{ name }}</button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'Button',
  props: {
    name: {
      type: String,
      required: true,
    },
  },
  setup(props, { emit }) {
    const clickAction = () => {
      //   alert('stop clicking me')
      emit('action')
    }

    return { clickAction }
  },
})
</script>
