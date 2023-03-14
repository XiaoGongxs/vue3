<template>
    <div>
        <h2>我是子组件 {{ fatherData }}</h2>
        <p>{{ money }}</p>
        <button @click="changeMoney">子传父组件通信</button>
    </div>
    <div>
        <GrandSon />
    </div>
</template>

<script>
import { inject } from 'vue';
import GrandSon from './组件通信GrandSon.vue'
export default {
    name: 'Son',
    props: {
        money: {
            type: Number,
            default: 0
        }
    },
    components: {
        GrandSon
    },
    setup(props, context) {
        // 在setup中获取父组件传过来的值
        console.log('子组件setup中获取props', props.money);
        // 使用setup中的第二个对象获取emit，用来触发父组件的事件传递参数
        // 第二个context也可以写成{emit}
        const changeMoney = () => {
            context.emit('change-money', 50)
        }
        // 后代组件中使用inject('exportData')接受父组件暴露的数据
        const fatherData = inject('exportData')
        return { changeMoney, fatherData }
    }
}
</script>