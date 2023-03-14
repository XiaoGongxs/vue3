<template>
    <div>
        <p>监听count的值 {{ count }}</p>
        <button @click="add">修改count值</button>
    </div>
    <div>
        <p>{{ obj.name }}</p>
        <button @click="updateName">修改名字</button>
    </div>
    <div>
        <p>{{ obj.list[0].name }}</p>
        <button @click="updateListName">修改列表中的名字</button>
    </div>
</template>

<script>
import { reactive, ref, watch } from 'vue'
export default {
    name: 'App',
    setup() {
        const count = ref(0)
        const add = () => {
            count.value++
        }
        // 1.当你需要监听一个数据的变化时候可以使用watch
        // 监听一个ref数据
        // watch第一个参数是你需要监听的值，第二个是改变后触发的函数
        watch(count, (newVal, oldVal) => {
            console.log(newVal, oldVal);
        })
        const obj = reactive({
            name: 'zs',
            age: 18,
            list: [
                { id: 1, name: '宝马' }
            ]
        })
        const updateName = () => {
            obj.name = 'ls'
        }
        const updateListName = () => {
            obj.list[0].name = 'ls'
        }
        watch(obj, () => {
            console.log('数据发生改变了');
        })
        // 深度监听对象中的属性(对象属性为其他复杂类型数据)
        // deep:开启深度监听，immediate立刻自动触发一次侦听（默认执行）
        watch(() => obj.list, () => {
            console.log('只监听obj对象中的list');
        }, {
            deep: true,
            immediate: true
        })
        // 监听对象中的某一个属性发生变化，第一个参数需要使用函数返回
        // watch(() => obj.name, (newVal, oldVal) => {
        //     console.log(newVal, oldVal);
        // })
        // 监听多个值的时候，第一个参数需要使用数组的形式
        // watch([count, obj], (newVal, oldVal) => {
        //     console.log(newVal, oldVal);
        // })
        return { count, add, obj, updateName, updateListName }
    }
}
</script>

