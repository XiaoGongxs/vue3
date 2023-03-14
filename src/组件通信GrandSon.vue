<template>
    <div>
        <h3>我是孙组件 {{ fatherData }}</h3>
        <button @click="desModChange">后代组件修改值</button>
    </div>
</template>

<script>
import { inject } from 'vue';

export default {
    name: 'GrandSon',
    setup() {
        // 后代组件中使用inject('exportData')接受父组件暴露的数据
        // 接受到的值不能直接修改(单向数据流的原则)
        const fatherData = inject('exportData')
        // 可以通过父组件暴露的方法，通过子组件触发父组件的方法修改通知父组件改值
        // 父组件暴露的方法可以通过参数可以传参
        const changeExportData = inject('changeExportData')
        const desModChange = () => {
            changeExportData('后代组件改值')
        }
        return { fatherData, desModChange }
    }
}
</script>