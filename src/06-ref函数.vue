<template>
  <div>{{name}}</div>
  <div>{{age}}</div>
  <button @click="updateName">修改名字</button>
</template>

<script>
import { ref } from 'vue'
export default {
  name: 'App',
  setup() {
    // 1.ref通常定义简单数据类型的响应式数据
    const name = ref('xiaoming')
    const age = ref(18)
    const updateName = () => {
      name.value = 'xiaozhang'
    }
    // 2.ref也可以定义复杂数据类型
    // 比如发请求的时候我们不知道数据类型，可以使用ref(null)，即使返回的是复杂数据类型也可以
    // 但是要记得xxx.value
    // const data = ref(null)
    // setTimeout(() => {
    //     data.value = res.data
    // },1000)
    // 3.当我们明确知道值需要响应式的对象的时候使用reactive，其他情况使用ref 
    return { name, age, updateName }
  }
}
</script>

<style>
</style>