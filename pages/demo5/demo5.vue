<template>
	<view>
		<User_layout >
			<template #header>
				<view class="header">上层区域</view>
			</template>
			<template #main>
				<view class="main">主体区域</view>
			</template>
			<template #footer>
				<view class="footer">底部区域</view>
			</template>
		</User_layout>
	</view>
</template>

<script setup>
	import User_layout from '@/components/user_layout/user_layout.vue';
	import { ref,computed } from 'vue';
	const shouming = ref('用户')
	const shouming_computed = computed(() => {
		return shouming.value + '的布局'
	})
</script>

<style lang="scss" scoped>
.header{
		height: 100rpx;
		line-height: 100rpx;
		text-align: center;
		color: #fff;
	}
.main{
		height: 200rpx;
		line-height: 200rpx;
		text-align: center;
		color: #fff;
	}
.footer{
		height: 100rpx;
		line-height: 100rpx;
		text-align: center;
		color: #fff;
	}
</style>