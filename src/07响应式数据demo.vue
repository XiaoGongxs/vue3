<template>
  <div>{{obj.x}}</div>
  <div>{{obj.y}}</div>
  <div>{{a}}</div>
  <button @click="addNumber">变量+1</button>
</template>

<script>
import { reactive, onMounted, ref } from 'vue'
export default {
  name: 'App',
  setup() {
    let obj = reactive({
      x: 0,
      y: 0
    })
    let a = ref(0)
    const addNumber = () => {
      a.value++
    }
    onMounted(() => {
      document.addEventListener('mousemove', (e) => {
        obj.x = e.screenX
        obj.y = e.screenY
      })
    })
    return { obj, a, addNumber }
  }
}
</script>

<style>
</style>