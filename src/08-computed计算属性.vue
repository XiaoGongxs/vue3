<template>
    <div>今年我{{ age }}岁</div>
    <div>后年我{{ newAge }}岁</div>
    <input type="text" v-model="newAge" />
</template>

<script>
import { computed, ref } from 'vue'
export default {
	name: 'App',
	setup() {
		const age = ref(18)
		// 计算属性，当你依赖当前现有的响应式数据，根据一定逻辑得到现有的结果
		// const newAge = computed(() => {
		//   // 该函数的返回值就是计算属性的值
		//   return age.value + 2
		// })

		const newAge = computed({
			// get函数，获取计算属性的值
			get() {
				return age.value + 2
			},
			// set函数，当给你的计算属性设置值的时候触发这里是newAge
			//这里set的value就是你修改的值
			// 计算属性支持v-model双向绑定
			set(value) {
				age.value = value - 2
			},
		})
		return { age, newAge }
	},
}
</script>

<style>

</style>
