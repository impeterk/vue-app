<template>
  <div class="home">
    <h2 ref="appTitleRef">{{ appTitle }}</h2>
    <h3>{{ counterData.counterTitle }}:</h3>
    <div>
      <button @click="decrement" class="btn">-</button>
      <span class="counter">{{ counterData.count }}</span>
      <button @click="increment" class="btn">+</button>
    </div>
    <p>This counter is {{ oddOrEven }}</p>
    <div class="edit">
      <h4>Edit title:</h4>
      <input v-model="counterData.counterTitle" type="text" v-autofocus />
    </div>
  </div>
</template>

<script setup>
import { reactive, computed, watch, ref, onMounted, nextTick } from 'vue'

const appTitle = 'My amazing Title'

const appTitleRef = ref(null)

onMounted(() => {
  console.log(`The app title is ${appTitleRef.value.offsetWidth} px wide`)
})

const counterData = reactive({
  count: 0,
  counterTitle: 'My counter'
})

watch(
  () => counterData.count,
  async (newCount) => {
    if (newCount == 5) {
      await nextTick()
      console.log('dom has updated')
    }
  }
)

const oddOrEven = computed(() => {
  if (counterData.count % 2 === 0) return 'even'
  return 'odd'
})

const increment = () => {
  counterData.count++
}

const decrement = () => {
  counterData.count--
}

// directives

const vAutofocus = {
  mounted: (el) => {
    el.focus()
  }
}
</script>

<style>
.home {
  text-align: center;
  padding: 2em;
}
.btn,
.counter {
  font-size: 2em;
  margin: 0.25em;
  padding-inline: 1em;
}
.edit {
  margin-top: 1em;
}
</style>
