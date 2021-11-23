<template>
  <div class="clock" :style="styledFontColor">
    <div class="ref">
      USING REF
      <div>{{ timeRef }}</div>
    </div>
    <h1 v-if="trigger">Vue is pretty cool</h1>
    <h1 v-else>😊</h1>
  </div>
</template>

<script lang="ts">
import {
  defineComponent,
  ref,
  computed,
  watch,
  // watchEffect,
} from 'vue'

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

    const styledFontColor = computed(() => {
      return 'color: ' + props.fontColor
    })

    const trigger = ref(false)
    // watchEffect(() => {
    //   console.log('watchEffect did something ' + props.fontColor)
    // })
    watch(
      () => props.fontColor,
      () => {
        trigger.value = trigger.value === false ? true : false
      }
    )

    return { timeRef, styledFontColor, trigger }
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
