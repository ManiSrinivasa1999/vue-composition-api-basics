<template>
  <div class="home">
    <h2>{{ appTitle }}</h2>
    <h3>{{ counterData.title }}:</h3>
    <div>
      <button class="btn" @click="decreaseCounter(2)">--</button>
      <button class="btn" @click="decreaseCounter(1)">-</button>
      <span class="counter">{{ counterData.count }}</span>
      <button class="btn" @click="increaseCounter(1, $event)">+</button>
      <button class="btn" @click="increaseCounter(2)">++</button>
    </div>
    <p>This counter is {{ oddOrEven }}</p>
    <div class="edit">
      <h4>Edit counter title:</h4>
      <input v-model="counterData.title" type="text" />
    </div>
  </div>
</template>

<script setup>
import {
  reactive,
  computed,
  watch,
  onBeforeMount,
  onBeforeUnmount,
  onMounted,
  onUnmounted,
  onActivated,
  onDeactivated,
  onBeforeUpdate,
  onUpdated,
} from 'vue'

const appTitle = 'My Amazing Counter App'
onMounted(() => {
  console.log('apptitle')
})

const counterData = reactive({
  count: 0,
  title: 'My Counter',
})

// watcher
watch(
  () => counterData.count,
  (newCount) => {
    if (newCount == 20) {
      alert('You reached 20')
    }
  }
)

// computed property
const oddOrEven = computed(() => {
  return counterData.count % 2 ? 'odd' : 'even'
})

// methods or functions
const increaseCounter = (amount, e) => {
  counterData.count += amount
}
const decreaseCounter = (amount) => {
  counterData.count -= amount
}
onMounted(() => {
  console.log('counter')
})

// life cycle hooks
onBeforeUpdate(() => {
  console.log('onBeforeUpdate')
})
onUpdated(() => {
  console.log('onUpdated')
})
onBeforeMount(() => {
  console.log('on before mount')
})
onMounted(() => {
  console.log('on mount')
})
onBeforeUnmount(() => {
  console.log('on before unmount')
})
onUnmounted(() => {
  console.log('on unmounted')
})
onActivated(() => {
  console.log('on activated')
})
onDeactivated(() => {
  console.log('on deactivated')
})
</script>

<style>
.home {
  text-align: center;
  padding: 20px;
}
.btn,
.counter {
  font-size: 40px;
  margin: 10px;
}
.edit {
  margin-top: 60px;
}
</style>
