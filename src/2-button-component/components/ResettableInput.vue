<template>
  <input type="text" name="2-way binding" id="input-field" v-model="value" />
  <button v-if="value !== ''" @click="action">reset</button>
  <div>{{ value }}</div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'

export default defineComponent({
  name: 'ResettableInput',
  setup() {
    const value = ref('text goes here')

    const action = () => {
      value.value = ''
    }

    return { value, action }
  },
})
</script>
