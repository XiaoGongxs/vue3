<template>
    <div>
        <p>我是子组件{{ modelValue }}</p>
        <button @click="changeValue">v-model语法糖</button>
    </div>
</template>

<script>
export default {
    name: 'Son',
    props: {
        modelValue: {
            type: Number,
            default: 0
        }
    },
    setup(props, { emit }) {
        const changeValue = () => {
            emit('update:modelValue', 100)
        }
        return { changeValue }
    }
}
</script>