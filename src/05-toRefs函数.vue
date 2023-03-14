<template>
  <div>{{name}}</div>
  <div>{{age}}</div>
  <button @click="updateValue">修改密码</button>
</template>

<script>
import { reactive, toRefs } from 'vue'
export default {
  name: 'App',
  setup() {
    // 1.响应式数据对象
    const obj = reactive({
      name: 'zs',
      age: 18
    })
    console.log(obj)
    // 2.解构或者展开数据对象得到的不是响应式数据
    // const { name, age } = obj
    // console.log(name, age)
    // const obj2 = { ...obj }
    // console.log(obj2)
    // 3.toRefs通常用于解构|展开reactive定义对象
    const { name, age } = toRefs(obj)
    const updateValue = () => {
        name.value = 'xiaoli',
        age.value = 20
    }
    console.log(name, age)
    return { name, age,updateValue }
  }
}
</script>

