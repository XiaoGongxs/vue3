<template>
  <div class="container">
    <h1 @click="fn()">{{msg}}</h1>
  </div>
</template>

<script>
export default {
  name: 'APP',
  //1.组合API的起点，将来的组合API的代码基本上在这里
  //2.setup在beforeCreate钩子执行前执行，组件实例创建前
  //3.函数中不能使用this == undefined
  //4.模板中需要使用的数据和函数，需要在setup中返回(retrun 一个对象将使用到的变量或函数放在里面)
  setup() {
    const msg = 'hi vue3'
    const fn = () => {
      console.log('hi vue3')
    }
    return { msg, fn }
    console.log(this)
  }
}
</script>

