<template>
	<view class="box">
		<input type="text"  v-model="inputValue" placeholder="请输入" />
		<input type="text"  v-model="person.name" placeholder="请输入姓名" />
		<input type="number"  v-model="person.age" placeholder="请输入年龄" />
	</view>
	{{ inputValue }}
	<view >{{ person }}</view>
	<view >
		<input type="text"  v-model="lastName" placeholder="请输入姓" />
		<input type="text"  v-model="firstName" placeholder="请输入名" />
		<view >全称：{{ fullName }}</view>
	</view>
	<view v-model="ii">{{ ii }}</view>
</template>

<script setup>
	import { ref } from 'vue';
	import { computed,watch,watchEffect } from 'vue';
		
	const i = ref(0);
	const ii = ref('李四');
	const inputValue = ref('');
	const lastName = ref('');
	const firstName = ref('');
	const fullName = computed(() => {
		return lastName.value + firstName.value;
	})
	const person = ref({
		name: '张三',
		age: 23
	})
	// 点击事件handleClick是点击按钮时触发的事件，内部包含inputValue.value的值
	// showToast是显示Toast的函数，参数title是显示的文本，参数icon是显示的图标
	// icon可以是'none'、'loading'、'success'、'error'、'none'
	const handleClick = () => {
		console.log(inputValue.value);
		uni.showToast({
			title: inputValue.value,
			icon: 'none'
		})
	}
	// 监听inputValue变化，当inputValue变化时，触发回调函数
	// 回调函数的参数newVal是新的值，参数oldVal是旧的值
	watch(inputValue, (newVal, oldVal) => {
		console.log(newVal, oldVal);
		// 当inputValue变化时，将新的值赋值给ii
		ii.value = newVal;
	})
	// 监听person变化，当person变化时，触发回调函数
	// 回调函数的参数newVal是新的值，参数oldVal是旧的值
	// deep: true 表示递归监听person对象的属性变化
	// immediate: true 表示在监听开始时立即触发回调函数
	watch(person, (newVal, oldVal) => {
		console.log(newVal, oldVal);
		// 当person变化时，将新的值赋值给ii
		ii.value = newVal;
	},{deep: true,immediate: true})
	// 监听lastName变化，当lastName变化时，触发回调函数
	// 回调函数的参数newVal是新的值，参数oldVal是旧的值
	watch(lastName, (newVal, oldVal) => {
		console.log(newVal, oldVal);
		// 当lastName变化时，将新的值赋值给ii
		ii.value = newVal;
	})
	// 监听firstName变化，当firstName变化时，触发回调函数
	// 回调函数的参数newVal是新的值，参数oldVal是旧的值
	watch(firstName, (newVal, oldVal) => {
		console.log(newVal, oldVal);
		// 当firstName变化时，将新的值赋值给ii
		ii.value = newVal;
	})
	// 监听fullName变化，当fullName变化时，触发回调函数
	// 回调函数的参数newVal是新的值，参数oldVal是旧的值
	watch(fullName, (newVal, oldVal) => {
		console.log(newVal, oldVal);
		// 当fullName变化时，将新的值赋值给ii
		ii.value = newVal;
	})
	// 监听ii变化，当ii变化时，触发回调函数
	// watchEffect是监听ii变化的函数，回调函数的参数ii.value是ii的当前值
	watchEffect(() => {
		console.log(lastName.value, firstName.value, fullName.value);
	})
</script>

<style lang="scss">
.box {
  width: 200px;
  height: 200px;
  background-color: #8a3636;
  font-size: 20px;
  color: #fff;
  text-align: center;
  line-height: 200px;
}
</style>