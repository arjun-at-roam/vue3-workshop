<template>
  <div class="clock" :style="styledFontColor">
    <div class="using-ref">
      USING REF
      <div>{{ timeRef }}</div>
    </div>
    <div class="using-reactive">
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
    const initialTime = new Date()
    const timeRef = ref(initialTime)
    const timeReactive = reactive({ value: initialTime })

    setInterval(() => {
      const currentTime = new Date()
      timeRef.value = currentTime
      timeReactive.value = currentTime
    }, 1000)

    const styledFontColor = computed(() => {
      return 'color: ' + props.fontColor
    })

    return {
      timeRef,
      timeReactive,
      styledFontColor,
    }
  },
})
</script>

<style scoped>
.clock {
  margin: 50px;
}
.using-ref {
  margin: 20px;
}
.using-reactive {
  margin: 20px;
}
</style>
