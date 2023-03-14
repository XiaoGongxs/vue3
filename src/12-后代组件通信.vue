<template>
    <div>
        <h1>我是父组件 {{ exportData }}</h1>
        <button @click="changeExportData('父组件改值')">修改传递给子组件的数据</button>
        <Son />
    </div>
</template>

<script>
import { provide, ref } from 'vue'
import Son from './组件通信Son.vue'
export default {
    name: 'App',
    components: {
        Son
    },
    setup() {
        const exportData = ref('父组件提供的数据')
        // 将父组件的数据提供给后代组件provide
        // 后代组件中使用inject('exportData')接受父组件暴露的数据
        provide('exportData', exportData)
        // 这里修改了传递给后代组件的值，显示在后代组件上的值也会发生改变
        const changeExportData = (value) => {
            exportData.value = value
        }
        // provide除了可以传递参数，还可以传递方法暴露给后代组件使用
        provide('changeExportData', changeExportData)
        return { exportData, changeExportData }
    }
}
</script>