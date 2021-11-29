<template>
  <div>
    <button class="buttonInput" v-if="show" @click="clickAction">
      {{ name }}
    </button>
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
      // default: 'default name',
    },
    show: {
      type: Boolean,
      default: false,
    },
  },
  setup(props, { emit }) {
    const clickAction = () => {
      emit('action')
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
