<template>
  <div class="clock" :style="styledFontColor">
    <div class="ref">
      USING REF
      <div>{{ timeRef }}</div>
    </div>
    <div class="reactive">
      USING REACTIVE
      <div>{{ timeReactive.value }}</div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, reactive, computed } from 'vue'

export default defineComponent({
  name: 'Clock',
  props: {
    fontColor: {
      type: String,
      required: true,
    },
  },
  setup(props) {
    // using ref
    const timeRef = ref(new Date())
    setInterval(() => {
      timeRef.value = new Date()
    }, 1000)

    // using reactive
    const timeReactive = reactive({
      value: new Date(),
    })
    setInterval(() => {
      timeReactive.value = new Date()
    }, 1000)

    const styledFontColor = computed(() => {
      return 'color: ' + props.fontColor
    })

    return { timeRef, timeReactive, styledFontColor }
  },
})
</script>
<style scoped>
.clock {
  margin: 10px;
}
.ref {
  margin: 20px;
}
.reactive {
  margin: 20px;
}
</style>
