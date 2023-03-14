<template>
    <div>
        <!-- 如果你想获取原生事件事件对象 -->
        <!-- 如果绑定是函数fn fn(e){e就是事件对象} -->
        <!-- 如果绑定的是js表达式 此时提供一个默认的变量$event -->
        <p @click="$event.target.style.color = 'red'">我是父组件{{ count }}</p>
        <!-- 如果你想获取自定义事件 -->
        <!-- 如果绑定是函数fn fn(data){data触发自定义事件的传参} -->
        <!-- 如果绑定的是js表达式，此时$event代表触发自定义事件的传参 -->
        <!-- <Son :modelValue="count" @update:modelValue="count = $event" /> -->
        <!-- 上面的语法糖简写 -->
        <Son v-model="count" />
    </div>
</template>

<script>
import { ref } from 'vue'
import Son from './v-model语法糖Son.vue'
export default {
    name: 'App',
    components: {
        Son
    },
    setup() {
        const count = ref(10)
        return { count }
    }
}
</script>

