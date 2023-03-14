<template>
  <div>{{name}}</div>
  <button @click="updateName">修改名字</button>
</template>

<script>
import { reactive, toRef } from 'vue'
export default {
  name: 'App',
  setup() {
    // 1.响应式数据对象
    const obj = reactive({
      name: 'zs',
      age: 18
    })
    console.log(obj)
    // 2.模板中只需要使用name数据
    // 3.从响应式数据对象中解构出来的值，不再是响应式数据
    // let { name } = obj 不能直接解构，解构出来的是一个普通数据
    let name = toRef(obj, 'name')
    console.log(name)
    const updateName = () => {
      console.log('updateName')
      // toRef转换成的数据包装成了对象，value存放值的位置
      //   使用场景，对象当中有一个响应式对象数据，但是dom模板中只使用一项
      name.value = 'xiaoli'
    }
    return { name, updateName }
  }
}
</script>

