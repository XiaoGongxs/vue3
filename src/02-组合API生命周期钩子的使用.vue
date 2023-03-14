<template>
  <div class="box">根组件</div>
</template>

<script>
// 生命周期调用需要导入
import { onBeforeMount, onMounted } from 'vue'
export default {
  name: 'App',
  setup() {
    //1.Dom渲染前的钩子
    onBeforeMount(() => {
      console.log('Dom渲染前的钩子', document.querySelector('.box'))
    })
    //2.Dom渲染后的钩子
    onMounted(() => {
      console.log('Dom渲染后的钩子1', document.querySelector('.box'))
    })
    //3.可以书写多个生命周期，书写不同的逻辑
    onMounted(() => {
      console.log('Dom渲染后的钩子2', document.querySelector('.box'))
    })
  }
}
</script>

<style>
</style>