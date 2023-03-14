<template>
    <div>{{ obj.name }}</div>
    <div>{{ obj.age }}</div>
    <button @click="updateName">修改名字</button>
</template>

<script>
import { reactive } from '@vue/reactivity'
export default {
  name: 'App',
  setup() {
    // 1.普通的复杂类型数据可以被直接渲染，但是无法驱动视图成为响应数据。
    // const obj = {
    //   name: 'xiaowang',
    //   age: 18
    // }
    // 2.使用reactive函数创建一个能够驱动视图的响应式数据
    // 通常是用来定义响应式对象数据
    const obj = reactive({
      name: 'xiaowang',
      age: 18
    })
    const updateName = () => {
      console.log('updateName')
      obj.name = 'xiaoli'
    }
    return { obj, updateName }
  }
}
</script>
