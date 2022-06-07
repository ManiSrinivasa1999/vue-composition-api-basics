<template>
  <div class="home">
    <h2>{{ appTitle }}</h2>
    <h3>{{ counterData.title }}:</h3>
    <div>
      <button class="btn" @click="decreaseCounter">-</button>
      <span class="counter">{{ counterData.count }}</span>
      <button class="btn" @click="increaseCounter">+</button>
    </div>
    <div class="edit">
      <h4>Edit counter title:</h4>
      <input v-model="counterData.title" type="text" />
    </div>
  </div>
</template>

<script setup>
import { reactive } from '@vue/reactivity'

const appTitle = 'My Amazing Counter App'

const counterData = reactive({
  count: 0,
  title: 'My Counter',
})

const increaseCounter = () => {
  counterData.count += 1
}
const decreaseCounter = () => {
  counterData.count -= 1
}
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

<!-- 
<script>
import { ref } from '@vue/reactivity'
export default {
  setup() {
    const counter = ref(0)
    const increaseCounter = () => {
      counter.value += 1
    }
    const decreaseCounter = () => {
      counter.value -= 1
    }

    return { counter, increaseCounter, decreaseCounter }
  },
}
</script>


<script>
export default {
  data() {
    return {
      counter: 0,
    };
  },
  methods: {
    increaseCounter() {
      this.counter += 1;
    },
    decreaseCounter() {
      this.counter -= 1;
    },
  },
};
</script>
-->