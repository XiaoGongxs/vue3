<template>
    <div>
        <h1>我是父组件</h1>
        <p>{{ money }}</p>
    </div>
    <hr>
    <Son :money="money" @change-money="updateMoney" />
</template>

<script>
import { ref } from 'vue'
import Son from './组件通信Son.vue'
export default {
    name: 'App',
    components: {
        Son
    },
    setup() {
        name: 'App'
        const money = ref(100)
        // 子组件触发父组件里的事件通过形参传递参数
        const updateMoney = (newMoney) => {
            console.log(newMoney);
        }
        return { money, updateMoney }
    }
}
</script>