<template>
  <div class="resettableInput">
    <input type="text" v-model="value" />
    <button v-if="value !== ''" @click="resetValue">reset</button>
    <div>{{ value }}</div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'

export default defineComponent({
  name: 'ResettableInput',
  setup() {
    const value = ref('')

    const resetValue = () => {
      value.value = ''
    }

    return { value, resetValue }
  },
})
</script>
<style scoped>
.resettableInput {
  margin: 20px;
}
</style>
