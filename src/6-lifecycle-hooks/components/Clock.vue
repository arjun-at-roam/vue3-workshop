<template>
  <div class="clock" :style="styledFontColor">
    <div class="time sydney">
      SYDNEY
      <div>{{ timeSyd }}</div>
    </div>
    <div class="time auckland">
      AUCKLAND/WELLINGTON
      <div>{{ timeAuck }}</div>
    </div>
    <div class="time singapore">
      SINGAPORE
      <div>{{ timeSing }}</div>
    </div>
  </div>
  <h1 v-if="trigger">Vue is pretty cool</h1>
  <h1 v-else>😊</h1>
</template>

<script lang="ts">
import {
  defineComponent,
  ref,
  computed,
  watch,
  // watchEffect,
  // onBeforeUpdate,
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
    // onBeforeUpdate(() => {
    //   console.log('onBeforeUpdate')
    // })
    const date = new Date()
    const tzSyd = 'Australia/Sydney'
    const tzAuck = 'Pacific/Auckland'
    const tzSing = 'Asia/Singapore'
    const timeSyd = ref(date.toLocaleString('en-AU', { timeZone: tzSyd }))
    const timeAuck = ref(date.toLocaleString('en-AU', { timeZone: tzAuck }))
    const timeSing = ref(date.toLocaleString('en-AU', { timeZone: tzSing }))

    setInterval(() => {
      timeSyd.value = new Date().toLocaleString('en-AU', {
        timeZone: tzSyd,
      })
      timeAuck.value = new Date().toLocaleString('en-AU', {
        timeZone: tzAuck,
      })
      timeSing.value = new Date().toLocaleString('en-AU', {
        timeZone: tzSing,
      })
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

    return { timeSyd, timeAuck, timeSing, styledFontColor, trigger }
  },
})
</script>
<style scoped>
.clock {
  display: flex;
  justify-content: center;
  margin: 30px 10px;
}
.time {
  width: 250px;
  font-weight: bold;
}
.ref {
  margin: 20px;
}
.reactive {
  margin: 20px;
}
</style>
