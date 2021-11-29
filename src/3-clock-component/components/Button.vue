<template>
  <div>
    <button class="buttonInput" v-if="show" @click="clickAction">
      {{ label }}
    </button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'Button',
  props: {
    label: {
      type: String,
      required: true,
      // default: 'default label',
    },
    show: {
      type: Boolean,
      default: false,
    },
  },
  setup(props, { emit }) {
    const clickAction = () => {
      emit('event')
    }

    return { clickAction }
  },
})
</script>

<style scoped>
.buttonInput {
  margin: 10px 5px;
}
</style>
