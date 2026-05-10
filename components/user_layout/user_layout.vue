<template>
	<view class="user_layout">
		<view class="header">header上层区域
			<slot name="header"></slot>
		</view>
		<view class="main">main主体区域
			<slot name="main"></slot>
		</view>
		<view class="footer">footer底部区域
			<slot name="footer"></slot>
		</view>
	</view>
</template>

<script setup>

</script>

<style lang="scss">
.user_layout{
	.header{
 	 height: 300rpx;
 	 background: #6f4b4b;
	}
	.main{
	  height: 300rpx;
	  background: #541d1d;
	}
	.footer{
	  height: 300rpx;
 	 background: #c82424;
	}
}

</style>