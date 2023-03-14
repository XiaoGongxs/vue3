<template>
    <div ref="box">我是box盒子</div>
    <ul>
        <li v-for="i in 4" :key="i" :ref="setList">我是第{{ i }}li</li>
    </ul>
</template>

<script>
import { onMounted, ref } from 'vue';

export default {
    setup() {
        // 1.使用ref函数获取dom元素
        const box = ref(null)
        console.log(box);
        // 1.1直接在setup中打印box.value值是获取不到dom的，setup在实例初始化之前
        onMounted(() => {
            console.log(box.value);
        })
        // 2.获取多个DOM元素
        const domList = []
        // 2.1获取多个DOM元素,使用函数去获取dom元素
        const setList = (el) => {
            domList.push(el)
        }
        console.log(domList);
        return { box, setList }
    }
}
</script>